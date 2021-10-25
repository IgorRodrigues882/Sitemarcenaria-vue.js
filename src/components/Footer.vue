<template>
     <div id='footer'>
        <footer>
            <div class='coluna'>
                <h1>Sobre nós</h1>
                <p>No mercado a mais de 60 anos, temos experiência
                 de sobra em atendimento e qualidade.
                     </p>
            </div>
            <div class="coluna">
                <h2>Contatos:</h2>
                <a href="https://www.instagram.com/marcenaria_versattil/" target="_blank"><i class="fab fa-instagram"></i></a>
                <a href="#"><i class="fab fa-facebook-f"> </i></a>
                <a href="#"><i class="fab fa-whatsapp"></i></a>
            </div>
            <div class="coluna">
                <h3>Onde estamos:</h3>
                <p>Rua Major Joviano Gomes Nº 99</p>
                <p>Bairro Oficinas Velhas</p>
                <p>Barra do Piraí-RJ</p>
            </div>
        </footer>
    </div>
</template>

<script>
export default {
    data() {
        
    },
}
</script>

<style>
    #footer{
        background-color: rgb(0, 0, 0);
        position: relative;
        bottom: 0;
         position: relative; 
        height: 200px;
        width: 100%;
        margin-top: -50px;
        margin:0 auto;
    }
    .coluna {
        display:inline; /*Evita o bug da margem duplicada*/
        width:200px;
        color: cadetblue;
        float: left;
        margin-left: 180px;
        
        }
        h1,h2,h3{
            font-family: Arial, Helvetica, sans-serif;
        }
        p{
            font-family: Arial, Helvetica, sans-serif;
        }
        .coluna a{
            font-size: 25px;
            padding: 10px;
            color:cadetblue;
            transition-duration: .4s;
        }

        .coluna a:hover{
       color: white;
        }
        
        @media only screen and (max-device-width:1000px) {
        #footer{height:500px;
        text-align: center;
        width: 100%;
        
        }
        .coluna{    
            margin: 0 auto;
            float: none;
            margin-top: 30px;
            
        }


        
    }

</style>