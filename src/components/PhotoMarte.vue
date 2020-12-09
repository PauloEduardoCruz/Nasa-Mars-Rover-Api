<template>
  <div>

        <div class="cartao">
            <div class="">
                <figure class="figura">
                    <img class="imgg" :src="img" alt="Placeholder image">
                </figure>
            </div>

            <div class="grid-tx">
                <div class="grid-titulo">
                    <p >{{camera}} </p> <br>
                    <p class="id"> ID: {{idNasa}} </p>
                </div>

                <div class="tx">
                    <p>Rover name: {{roverNome}} </p>
                    <p>Status: {{status}}</p>
                    <p>Lançamento: {{lancamento}}</p>
                    <p>Chegada: {{chegada}} </p>
                </div>
            </div>

        </div>

  </div>
</template>


<script>


export default {
    props:{
        img: String,
        idNasa: Number,
        camera: String,
        roverNome: String,
        status: String,
        lancamento: String,
        chegada: String
    }
}
</script>


<style>
.cartao{

    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;


    border-radius: 0.5rem;
    background-color: #5e5e5e00;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
    color: #ffffff;
    width: 30vw;
    height: auto;
    overflow: hidden;
    position: relative;


    border-bottom: 3px solid#48c774;
    border-top: 1px solid#ffffff;
    
}


.grid-titulo{
  display: flex;
  justify-content: space-between;
  border-bottom: 2px solid#48c774;
  
}

p {
    display: block;
    margin-block-start: 0em !important;
    margin-block-end: 0em !important;
    margin-inline-start: 0px !important;
    margin-inline-end: 0px !important;
}

.tx{
    text-align: initial;
    margin-top: 10%;
}

.imgg {
    height: 100%;
    width: 100%;
    object-fit: cover; 
}

.figura{
    width: 100%;
    height: 50vh;
}

.grid-tx{
    padding: 5% 10%;
}

.id{
    color: #48c774;
}



@media only screen and (max-width: 700px){
    .cartao {
        width: 95vw;
        margin-bottom: 10%;
    }
}
</style>