<template>
    <div class="orc">
       

            <fieldset >
        
            <form action="" method="POST">
              <label class="esptxt">Nos conte sua ideia:</label><br>
                <textarea name="especifique" id="esp" cols="50" rows="10"></textarea>
               <br>
               <label class="txtcont">Como podemos entrar em contato?</label>
               <br>
               <br> 
               
                <label class='labels'>Whatsapp:
                    <input type="checkbox" name="zap" id="zap" class="checkbox" style="display:none;" @click="inputtest=!inputtest"> 
                    <div class="ico">
                <i class="far fa-check-circle"></i></div>
                </label> 

                <transition name="slide-fade">  
                <input type="text" class='input-zap' id="telefone" v-if="inputtest" @keypress="masc" maxlength="14" placeholder="Whatsapp">
                </transition>
                <br><br>
                       
                <label class="labels">Email:
                    <input type="checkbox" name="email" id="e-mail" class="checkbox" style="display:none;" @click="inputtest2=!inputtest2">
                     <div class="ico">
                        <i class="far fa-check-circle"></i></div>
                </label>

                <transition name="slide-fade"> 
                <input type="text" class="inputs" id="email" v-if="inputtest2" placeholder="Email">
                </transition> <br><br>

                <label class="label-nome">Nome:</label>
                <input type="text" class="inputs" id="nome" placeholder="Nome">
                <br><br>

                <button type="submit" id="enviar">Enviar</button>
            </form>
            </fieldset>
        </div>
</template>

<script>


export default {
    data() {
        var larg=window.innerWidth;
        if(larg<720){
            return{
                 tela_responsiva:true,
                 inputtest2:false,
                 inputtest:false,
            }
        }
        return{
        tela_responsiva:false,
        inputtest2:false,
        inputtest:false,
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
            
        }

    }
        
}
</script>

<style scoped>
 textarea{
        resize:none;
        margin: 0 auto;
        border-radius: 10px;
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
        color: cadetblue;
        text-shadow: 0 0 15px cadetblue;
    }
    .orc{
        background-image: url("../assets/imagens/orcimage.jpg");
        background-repeat: no-repeat;
        width: 100%;
        background-size: cover;
        background-position: center;
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