<template>
<div id="app" @click="clickfechar">
  <cliente/>
      <input  type="checkbox" id="btn_menu" style="display : none">
      <label   for="btn_menu" id='menucel'>&#9776;</label>
      
         <nav id="nav_c">
            <ul>
                <div>
                    <li><a href="#"  @click="home">HOME</a></li>
                    <li><a href="#"  @click="servicos">FAÇA UM ORÇAMENTO</a></li>
                
                </div>
            </ul>
         </nav>
         <div class="social-medias" @scroll.passive="initreturn">
          <li><a href="#"> <i class="fab fa-facebook-f"> </i></a></li>
          <li><a href="#"> <i class="fab fa-whatsapp"></i></a></li>
              <li><a href="#"><i class="fab fa-instagram"></i></a></li>
         </div>

      <div id="seta" >
        <a href="#app" id="tg"><i class="fas fa-arrow-circle-up"></i></a>
      </div>
      
  <transition name='lenta' >       
  <home v-if="apareci"  :test="rolbar"></home> 
  </transition>

  <transition name='lenta'>
  <orcamentos v-if="contatos"></orcamentos>
  </transition>
 
  <Footer/>

</div>
</template>

<script>
import '@fortawesome/fontawesome-free/css/all.css'
import '@fortawesome/fontawesome-free/js/all.js'
import Cliente from './components/Cliente.vue'
import home from './components/home.vue'
import orcamentos from './components/orcamentos.vue'
import Footer from './components/Footer.vue'
export default {
  name: 'App',

  data()
  {
        return{
        apareci:true,
        trabalhos:false,
        contatos:false,
        cont:0,
        rolbar:0

    }

  },
  components: {
    Cliente,
    home,
    orcamentos,
    Footer,
    
    
  },

  
  methods:{
        home: function(){
            this.apareci=true
            this.contatos=false
        },
        servicos:function(){
            this.contatos=true
            this.apareci=false
            
        },
        /* Função para fechar menu responsivo ao clicar em qualquer lugar do documento */
        clickfechar:function(){
        this.cont+=1;
        if(this.cont==3){
          document.getElementById("btn_menu").checked=false;
          this.cont=0;} 
      },
      /* Função para ativar botão de rolagem */
      initreturn:function(){
        this.rolbar=document.body.scrollTop;
        if(this.rolbar>140){
          document.getElementById("seta").style.opacity="1";
        }
        else{document.getElementById("seta").style.opacity="0";}
      },
},
     
  mounted(){
    document.body.addEventListener('scroll',this.initreturn)
  },
  unmounted(){
    document.body.romoveEventListener('scroll', this.initreturn,);
    }
  
}



</script>

<style>

#app{
    margin: auto;
    padding-top: 0px;
    min-height: 100%;
  margin-bottom: -50px;
  }
  .social-medias{
    float:right;
    margin-top: -45px;
    margin-right: 10%;
    font-size: 25px;
    width: 250px;
    
  }
  #seta{
    font-size: 40px;
    position: absolute;
    z-index: 4;
    bottom: 40px;
    right: 40px;
    opacity: 0;
    transition: .4s;

  }
  #seta a{
    color: cadetblue;
  }
 
  .social-medias li{
    display: inline;
    padding: 25px;
  }
  .social-medias a{
    text-decoration: none;
    color: black;
    transition-duration: 0.4s;
  }
  .social-medias a:hover{
    color: cadetblue;
  }
  #nav_c{
    height: 60px;
    margin-top: -16px;
    width:60% ;
   
  }
  #nav_c li{
        display: inline-block;
        margin-top:16px;
        padding: -10px;

        
    }
    #nav_c a{
        font-size: 1em;
        text-decoration: none;
        color: black;
        margin: 40px;
        font-family: Arial, Helvetica, sans-serif;
        transition-duration: .4s;
        font-weight: 600;
        letter-spacing: 0.05em;
        
    }
    #nav_c a:hover{
    background-color: cadetblue;
    border-radius: 5px;
    padding: 10px 5px;
    margin: 35px;
    }
    label[for='btn_menu']{
        padding: 15px;
        font-size: 35px;
        font-family: arial;
        position: absolute;
        color:cadetblue;
        z-index: 5;
        display: none;
    }
    input[type=text]{
        border-radius: 5px;
    }
    
   
 .lenta-enter-from{
   opacity: 0;
 }
 .lenta-enter-to{
   opacity: 1;
 }
 .lenta-leave-from{
   opacity: 1;
 }
 .lenta-leave-to{
   opacity: 0;
 }
 .lenta-leave-active,.lenta-enter-active {
   transition: all .5s ease;}
 
  
    @media only screen and (max-device-width:800px){
      #nav_c{
      background-color: rgb(0,0,0,0.6);
      height: 100%;
      margin-left: -100%;
      width: 350px;
      position: absolute;
      margin-top: -90px;
      z-index: 3;
      transition: all .4s;
      
      }
      #nav_c li{
        margin-bottom: 10px;
      }
      #nav_c ul{
        list-style: none;
      margin-top: 50px;
      }
      #nav_c a{
      display: block;
      padding: 5px 5px;
      text-decoration: none;
      color: white;
      font-weight: 700;
      }
      label[for='btn_menu']{
        display: block;
        position: relative;
        width: 35px;
      }
      #nav_c a:hover{
        background-color: black;
        border-radius: 0px;
        

      }
      
      #btn_menu:checked ~ #nav_c{
        margin-left:0 ;

      }
    
    }
   
</style>