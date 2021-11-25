<template>
 <div class="div-home">
            <div class="slider">
                <splide :options="options">
                <splide-slide>
                    <img class="img-responsiva" src="../assets/imagens/marce1.jpg">
                </splide-slide>
                <splide-slide>
                    <img class='img-responsiva' src="../assets/imagens/marce2.jpeg">
                </splide-slide>
                <splide-slide>
                    <img class="img-responsiva" src="../assets/imagens/Marce3.jpg">
                </splide-slide>
                </splide>
            </div>
            <div class='cards'>
                <div class="box">
                    <span></span>
                    <div class="content">
                        <h2>Nossa história</h2>
                        <hr>
                            <p class="txt-p">
                                Nossa história começa no estado do Paraná,
                                quando aos 4 anos de idade, Francisco Pereira Gabriel começou a trabalhar com seu pai na marcenaria da família. Desde então Francisco (Gabriel) vem durante seus 64 anos atuando em sua marcenaria. A marcenaria versáttil. 
                             </p>
                    </div>
                 </div>
                 <div class="box">
                     <span></span>
                     <div class="content">
                        <h2>Nossos valores</h2>
                        <hr>
                        <p class="txt-p">
                            Honrar todos os compromissos firmados, prestar sempre o melhor serviço, nunca atrasar nenhum compromisso.
                        </p>
                     </div>
                 </div>
                 <div class="box">
                     <span></span>
                     <div class="content">
                        <h2>Materiais que usamos </h2>
                        <hr>
                        <p class="txt-p">
                            Toda madeira que usamos são legalizadas e da melhor qualidade, assim como também as ferragens como dobradiças, corrediças etc.
                        </p>
                    </div>
                 </div>
            </div>
            <h1>Alguns trabalhos</h1>
            <div class="camada1">
                <div id="foto">
                    <div id="hello">
                        <div id="carrousel" v-for="teste in teste" :key="teste">
                        <img :src="teste.src" class="img-style">
                        <p>{{teste.descricao}}</p>
                        </div>
                    </div>
               
                </div>
                <a class="esq" href="#" @click="moveCarrousel(-1)"><i class="fas fa-chevron-left"></i></a>

                 <a class="dir" href="#" @click="moveCarrousel(1)" ><i class="fas fa-chevron-right"></i></a>
            </div>
            <transition name="animation">
            <div id="animacao-1" >
                <img src="../assets/imagens/mdfverde.jpg" alt="">
                <p>Aqui você encontrará os melhores preços com a melhor qualidade!! E tudo isso com 8 anos de garantia!</p>
            </div>
            </transition>

            <div class="avaliacoes">
                <h2>Nos avalie</h2>
                <a href="#" id="star" v-for="estrelas in estrelas" :key="estrelas" @click="avaliacao(estrelas)" ><i class="fas fa-star" :id="estrelas"  ></i></a>
                    
                <br><br>
                <transition name="form">
                <div class="comentario" v-if="formav">
                    <a href="#" class="fechar" @click="fechar">X</a>
                        <input type="text" name="nome" id="nome" placeholder="Nome">
                        <br>
                        <br>
                        <br>
                        <br>
                        <label><p> Sua avaliação:</p>
                            <br>
                        <textarea name="comentario" id="coment" cols="30" rows="10"></textarea>
                        </label>
                        <br>
                        <a href="#" class="enviar" @click="adicionarcoment()">Enviar</a>
                        
                </div>
                </transition>
            </div>     
                <br>
                <br>
                <div class="nos_avalie">
                        <div class="notas" v-for="index in index" :key="index.id">
                             <a href="#" v-for="nota in index.nota" :key="nota"><i class="fas fa-star" ></i></a>
                            <h1>{{index.nome}}</h1>
                            <p>{{index.msg}}</p>
                        </div>
                </div>
          <div class='localizacao'>
                  <h1>Onde estamos:</h1>
                <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d921.6694279236502!2d-43.838430970842836!3d-22.478742359867145!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x9eb4521d9b215b%3A0x7c49ce43781aeab1!2sR.%20Maj.%20Joviano%20Gomes%2C%2099%20-%20Oficina%20Velha%2C%20Barra%20do%20Pira%C3%AD%20-%20RJ%2C%2027110-120!5e0!3m2!1spt-BR!2sbr!4v1631465600868!5m2!1spt-BR!2sbr"  style="border:0;" allowfullscreen="" loading="lazy"></iframe>  
            </div>  
        </div>
    
</template>

<script>
import '@splidejs/splide/dist/css/themes/splide-sea-green.min.css';
import{ Splide, SplideSlide } from '@splidejs/vue-splide';
export default {
    props:{
        test: Number
    },
     components: {
    Splide,
    SplideSlide,
  },
    data() {
        return{
            options: {
             height:'50%',   
             rewind : true,
             width  : '100%',
             gap    : '1rem',
             autoplay: true,
             interval:4000,
             arrows:false,
             type: 'fade'},
             currentOffset: 0,
             paginationFactor: 310,
             estrelas:5,
             formav:false,
             click:0,
             teste:[
                 {src:require('../assets/imagens/marce4.jpg'),
                 descricao:'ldldlld'
                 },
                 {
                    src:require('../assets/imagens/marce5.jpg'),
                     descricao:'ldldlld' 
                 },
                 {
                    src:require('../assets/imagens/marce6.jpg'),
                     descricao:'ldldlld' 
                 },
                 {
                     src:require('../assets/imagens/marce7.jpg'),
                     descricao:'ldldlld' 
                 },
                 {
                     src:require('../assets/imagens/marce7.jpg'),
                     descricao:'ldldlld' 
                 }
             ],

             index:[
                 {
                     id:1,
                     nome:'Igor Rodrigues',
                     msg:'Excelente serviço, entrega feita na data correta e bom preço!',
                     nota:5
                 }
             ],
             nextindex:2,
             vercoment:false,



                       
         }
    },
    
   
    methods:{
        moveCarrousel:function(direcao){
            if(direcao==1){
                this.currentOffset -= this.paginationFactor;
                
            }
            else if(direcao== -1){
                this.currentOffset+=this.paginationFactor;
                
             }
             if(this.currentOffset>310){this.currentOffset=310;}
             else if(this.currentOffset<-620){this.currentOffset=-620}
            document.getElementById("hello").style.transform='translateX' + '(' + this.currentOffset + 'px' + ')'
        },

    //Método para "acender" as icons de estrela. O ID das icons foi definido usando o v-for. Sendo assim fica: id="1",id="2" etc... 
        avaliacao:function(valor){
            this.nota=valor;
            this.formav=true;
            for(this.cont=1; this.cont<=valor; this.cont++){
                document.getElementById(this.cont).style.color="darkgoldenrod"
                for(this.i=1;this.i<=this.estrelas; this.i++){
                    if(this.i>valor){
                       document.getElementById(this.i).style.color="darkgray" 
                    }
                    }
                }
            },
        fechar:function(){
                this.formav=false;
                for(this.i=1;this.i<=this.estrelas; this.i++){
                       document.getElementById(this.i).style.color="darkgray" 
                    }
            },
        adicionarcoment(){
            this.index.push({
                id:this.nextindex++,
                nome:document.getElementById("nome").value,
                msg:document.getElementById("coment").value,
                nota:this.nota
            })
            this.index.sort((a,b)=>b.id-a.id)

        }
    
    },

}

</script>

<style >
@import '../stylehome.css';
</style>