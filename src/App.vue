<template>
  <div id="app">


    <div class="grid-master">
      <div v-for="photo in filterMarsRover" :key="photo.img_src">
        <PhotoMarte :img="photo.img_src" :idNasa="photo.id" :camera="photo.camera.full_name"
         :roverNome="photo.rover.name" :status="photo.rover.status"
         :lancamento="photo.rover.launch_date" :chegada="photo.rover.landing_date" />
      </div>
    </div>

    <button @click="buscar()" class="button buscaBtn is-success">Atualizar</button>

    <p class="links"> 
        <a href="https://www.linkedin.com/in/paulo-eduardo-s-da-cruz-3773bb154/">Dev by Paulo Cruz /</a>
        <a href="https://vuejs.org/"> Vue.js /</a>
        <a href="https://api.nasa.gov/"> Nasa - Mars Rover Api </a>
    </p>

  </div>
</template>

<script>

  import axios from 'axios';

  import PhotoMarte from './components/PhotoMarte'

  export default {
    name: 'App',
    components: {
      PhotoMarte
    },
    data(){
      return {
        marsRover: [],
        filterMarsRover: [],
        numeros: [],
      }
    },
    created: function(){

      this.aleat();
      //axios.get("qqq")
      
      axios.get("https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1500&api_key=CO6UsrsopOI0K5peyjztdXiIAh4iz9j02df0UiU6").then(res => {
          this.marsRover = res.data.photos
          for(let i in this.numeros){
            this.filterMarsRover.push(this.marsRover[this.numeros[i]])
          }
          console.log(this.marsRover)
          console.log(this.filterMarsRover)
      })
    
    },



    methods: {
      buscar: function(){
        this.aleat();

        this.filterMarsRover = []
          for(let i in this.numeros){
            this.filterMarsRover.push(this.marsRover[this.numeros[i]])
          }
      },




      aleat: function(){
        this.numeros= [];
        while (this.numeros.length < 2) {
          var aleatorio = Math.floor(Math.random() * 200);
          if (this.numeros.indexOf(aleatorio) == -1)
              this.numeros.push(aleatorio);
        }
        console.log("Aleatorios: ",this.numeros)
      }


    },
    computed: {

    }
  }
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;


  min-height: 100vh;

    background: linear-gradient(to bottom, rgba(255,255,255,0.15) 0%, rgba(255, 255, 255, 0.15) 100%), radial-gradient(at top center, rgba(255,255,255,0.40) 0%, rgb(0 0 0) 120%) #505050;
    background-blend-mode: multiply,multiply;
}


.grid-master{
  min-height: 90vh;

  display: flex;
  justify-content: space-around;
  align-items: center;

}

a {
  margin-top: 100px;
  color: inherit  !important; /* blue colors for links too */
  text-decoration: inherit !important; /* no underline */
}
.links{
  text-align: start;
}


@media only screen and (max-width: 700px){
    .grid-master{
        display: flex;
        flex-direction: column;
    } 
}
</style>
