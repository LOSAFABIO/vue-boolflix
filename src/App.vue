<template>
  <div id="app">
    <Header @getSerieFilm="getDataApi"/>
    <Main :listFilms="filmArray" :listSeries="serieArray"/>
  </div>
</template>

<script>
import Main from "./components/Main.vue";
import Header from "./components/Header.vue";
import axios from "axios";

export default {
  name: 'App',
  components: {
    Main,
    Header
  },
  data(){
      return {
      filmArray  : [],
      serieArray : [],
      apiURL     : "https://api.themoviedb.org/3/search/movie/",
      apiURL2    : "https://api.themoviedb.org/3/search/tv/",
      inputApp   : ""
      }
  },
  methods:{
    getDataApi (filtroApp){
      this.inputApp = filtroApp
      this.getFilmSerie()
      console.log(this.inputApp)
    },
    getFilmSerie(){
        axios.get(this.apiURL, {
          params : {
            api_key : "a39afba29712edaa4c2865fea35ce64f",
            query   : this.inputApp
          }
        })
        .then((risposta) => {
          // handle success
          this.filmArray = risposta.data.results;
          this.select = ""
          console.log(this.filmArray)
        })
        .catch(function (error) {
            // handle error
            console.log(error);
        }),

        axios.get(this.apiURL2, {
          params : {
            api_key : "a39afba29712edaa4c2865fea35ce64f",
            query   : this.inputApp
          }
        })
        .then((risposta2) => {
          // handle success
          this.serieArray = risposta2.data.results;
          this.select = ""

          console.log(this.serieArray)
        })
        .catch(function (error) {
            // handle error
            console.log(error);
        })
    }
  }
}
</script>

<style lang="scss">

@import "./assets/style/Globals.scss";

</style>
