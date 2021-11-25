<template>
    <div class="orc" @click="fechar_submit">
       

            <fieldset >
        
            <form action="" @submit.prevent="verifica_contatos" @submit="submit" method="POST">
              
               <label class="txtcont">Escolha por onde entraremos em contato:</label>
               <br>
               <br>
               <br> 
               
                <label class='labels'>Whatsapp:
                    <input type="checkbox" name="zap" id="zap" class="checkbox" style="display:none;" @click="inputtest=!inputtest" v-model="inputtest"> 
                    <div class="ico">
                <i class="far fa-check-circle"></i></div>
                </label> 

                <transition name="slide-fade">  
                <input type="text" class='input-zap' id="telefone" v-if="inputtest" @keypress="masc(); verifycontatos=false" maxlength="13" placeholder="Whatsapp">
                </transition>
                <br><br>
                       
                <label class="labels">Email:
                    <input type="checkbox" name="email" id="e-mail" class="checkbox" style="display:none;" @click="inputtest2=!inputtest2" v-model="inputtest2">
                     <div class="ico">
                        <i class="far fa-check-circle"></i></div>
                </label>
                    
                <transition name="slide-fade"> 
                <input type="text" class="inputs" id="email" v-if="inputtest2" @keypress="verifycontatos=false" placeholder="Email">
                </transition> <br><br>

                <label class="label-nome">Nome:</label>
                <input type="text" class="inputs" id="nome" placeholder="Nome">
                <br><br><br>
                <label class="esptxt">Nos conte sua ideia:</label><br>
                <textarea name="especifique" id="esp" cols="50" rows="10" @keypress="contador+=1" @keydown.delete="assistecontador" required></textarea>
                <p class="contadora">{{contador}}</p>
                <button id="enviar" >Enviar</button>
            </form>
            <transition name="msg_alert">
            <div class="alert" v-if="verifycontatos">
                <p>{{texto_alert}}</p>
            </div>
            </transition>
            
            </fieldset>
            <transition name="anime-sucesso">
            <div class="sucesso" v-if="sucesso">
                <i class="far fa-check-circle"></i>
                <p>Orçamento enviado!</p>
            </div>
            </transition>
        </div>
</template>

<script>


export default {
    data() {
        return{
        texto_alert:"Escolha uma das opções (ou as duas) para que possamos entrar em contato",
        inputtest2:false,
        inputtest:false,
        contador:0,
        verifycontatos:false,
        sucesso:false,
        }
        
    },
    methods:{
        // Máscara para inserir "(  )" entre o ddd do telefone 
         masc:function(){
            this.tel=document.getElementById("telefone").value.length;
            
            if(this.tel==0){
              document.getElementById('telefone').value='('+ document.getElementById("telefone").value;
            }
            if(this.tel==3){
             document.getElementById("telefone").value= document.getElementById("telefone").value +')';
            }       
            
        },
        teste_telefone:function(number){
            this.regex= new RegExp('^\\([0-9]{2}\\)(9[0-9]{8})$')
            if(!this.regex.test(number)){
                this.texto_alert="Número inválido"
                return true  
            }
            else return false;

        },
        teste_email:function(email){
            this.regex= new RegExp('^[a-zA-Z0-9_.-]+@[a-zA-Z0-9-]+.[a-zA-Z0-9-.]+$')
            if(!this.regex.test(email)){
                this.texto_alert="Email inválido";
                return true;
            }
            else return false;
        },
        assistecontador:function(){
                this.contador-=1;
                if(this.contador<0){
                    this.contador=0;
                }
        },

        // Função para validação do email e número de telefone
        verifica_contatos:function(){
            if(this.inputtest2==false && this.inputtest==false){
                this.verifycontatos=true;    
            }
            else if(this.inputtest2==true && this.inputtest==true){
                this.email=document.getElementById("email").value;
                this.zap=document.getElementById("telefone").value;
                    if(this.teste_telefone(this.zap)|| this.teste_email(this.email)){
                        this.verifycontatos=true;
                    }
                    else this.verifycontatos=false
            }
            else if(this.inputtest==true && this.inputtest2==false){
                this.zap=document.getElementById("telefone").value;
                    if(this.teste_telefone(this.zap)){
                        this.verifycontatos=true;
                    }
                    else this.verifycontatos=false
            }
             else if(this.inputtest==false && this.inputtest2==true){
                this.email=document.getElementById("email").value;
                    if(this.teste_email(this.email)){
                        this.verifycontatos=true;
                    }
                    else this.verifycontatos=false
             }

            else this.verifycontatos=false;
        },
      
        submit:function(){
            if(this.verifycontatos==false){
                this.sucesso=true
                
            }
        },
        // função para fechar div de validação de envio do formulário
        fechar_submit(){
            if(this.sucesso==true){
                this.sucesso=false;
                if(this.inputtest){
                document.getElementById("telefone").value="";
                this.inputtest=false
                }
                if(this.inputtest2){
                document.getElementById("email").value="";
                this.inputtest2=false
                }

                document.getElementById("esp").value="";
                this.contador=0;
                document.getElementById("nome").value="";


            }
        }


    },
        
}
</script>

<style scoped>
 textarea{
        width: 75%;
        resize:none;
        margin: 0 auto;
        border-radius: 10px;
        height: 150px;
        font-size: 16px;
        font-family: Arial, Helvetica, sans-serif;
    }
    textarea:hover{
        border: 1px solid cadetblue;
    }
    .ico{
        cursor: pointer;
        float: left;
        margin-right: 10px;
        color:grey
    }
    .ico:before{
        content: '';
        position: absolute;
        top:2px;
        left: 2px;
    }
    input[type="checkbox"]:checked ~ .ico .fa-check-circle{
        color: rgb(7, 245, 7);
        text-shadow: 0 0 15px cadetblue;
    }
    .orc{
        background-image: url("../assets/imagens/orcimage.jpg");
        background-repeat: no-repeat;
        width: 100%;
        background-size: cover;
        background-position: center;
        justify-content: center;
        align-items: center;
        display: flex;
    }
    fieldset{
        background-color: rgb(0,0,0,0.6);
        width: 800px;
        margin:auto;
        border: none;
        text-align: center;
    }
    form{
        padding: 10px;
        width: 500px;
        margin:0 auto ;
        

    }
    .txtcont{
        margin:0 auto;
       font-size: 26px;
        font-family: 'Times New Roman', Times, serif;
        color: #e5e5e5;
        margin-top: 0;

    }
    .input-zap{
         line-height: 25px;
        border-radius: 6px;
        padding: 0 22px;
        font-size: 16px;
        border: none;
        float: left;
        margin-left: 24px;
    }

    .inputs{
        line-height: 25px;
        border-radius: 6px;
        padding: 0 22px;
        font-size: 16px;
        border: none;
        float: left;
        
        margin-left: 55px;
    }
    .label-nome{
        color: #e5e5e5;
        text-transform: capitalize;
        font-family:'Times New Roman', Times, serif;
        font-size: 20px; 
        float: left;
        margin-left: 88px;
    }
    .labels{
        color: #e5e5e5;
        text-transform: capitalize;
        font-family:'Times New Roman', Times, serif;
        font-size: 20px; 
        float: left;
        margin-left: 60px;  
    }
    .contadora{
        color: white;
        font-size: 0.8em;
        margin-left: 70%;
        margin-top:0 ;
        padding: 0;
    }
    .alert{
        width: 130px;
        float: left;
        height: 70px;
        background-color: red;
        margin-top: -455px;
        margin-left: 50px;
        z-index: 100;
        border-radius: 10px;
    }
    .alert::before{
         content: "";
         width: 0; 
        height: 0;
        position: absolute;
        margin-top: 15px;
        margin-left: 58px;
        border-top: 20px solid transparent;
        border-bottom: 20px solid transparent;
        border-left: 20px solid red;
        border-radius: 50%;
        z-index: 4000;
    }
    .alert p{
        font-size: 0.7em;
        color: white;
        margin-right: 6px;

    }
    .sucesso{
        width: 300px;
        height: 300px;
        z-index: 5000;
        background-color: rgb(59, 165, 59);
        border-radius: 15px;
        text-align: center;
        margin: 0 auto;
        position: absolute;
        box-shadow: 3px 2px 2px 3px rgba(0,0, 0, 0.3);
    }
    .sucesso p{
        color: honeydew;
        font-size: 1.5em;
        margin-top: 10%;
    }
    .sucesso .fa-check-circle{
        margin-top: 30%;
        font-size: 5.0em;
        color:honeydew ;
    }
    
    button{
        
        border-radius: 10px;
        border:2px solid cadetblue;
        color: black;
        padding: 16px 32px;
        text-align: center;
        text-decoration: none;
        font-size: 16px;
        margin: 4px 2px;
        cursor: pointer;
        transition-duration: 0.4s;
        margin-top: 35px;
        
    }
    button:hover{
        background-color: cadetblue;   
    }
    .esptxt{
        font-size: 26px;
        font-family: 'Times New Roman', Times, serif;
        color: #e5e5e5;
    }

     .slide-fade-enter-active {
         transition: all .3s ease;
        }
    .slide-fade-leave-active {
    transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
    }
    .slide-fade-enter-from, .slide-fade-leave-to
    /* .slide-fade-leave-active em versões anteriores a 2.1.8 */ {
    transform: translateX(10px);
    opacity: 0;
}


    .msg_alert-enter-active{
        transition: all .3s ease;
    }
    .msg_alert-leave-active{
        transition: all .3s cubic-bezier(1.0, 0.5, 0.8, 1.0);
    }
    .msg_alert-enter-from, .msg_alert-leave-to
    /* .slide-fade-leave-active em versões anteriores a 2.1.8 */ {
    transform: translateX(-10px);
    opacity: 0;
}

@media only screen and (max-device-width:800px){
    .inputs{
         line-height: 10px;
    }
    .orc{
        height: 100%;
    }
    fieldset{
        width: 90%;
    }
    textarea{
        width: 90%;
    }
    form{
        width: 100%;
        text-align: center;
    }
    .labels{
        font-size: 15px;
        width: 30px;
    }
    .inputs, .input-zap{
        width: 50%;
        line-height: 25px;
        font-size: 10px;
    }
    .input-zap{
        margin-left: 55px;
    }

}
</style>