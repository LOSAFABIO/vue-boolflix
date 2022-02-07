<template>
  <div class="container">
    <div class="container-movies">
        <Cerca 
        @filtra="getFilmSerieAncora"
        />
    </div>
  </div>
</template>

<script>

import Cerca from "./commons/Cerca.vue";
// import axios from "axios";

export default {
  name: "Header",
  components : {
    Cerca
  },
  data(){
    return{
      getSerieFilm : ""
    }
  },
  methods : {
    getFilmSerieAncora(getFilmSerie){
      this.$emit(`getSerieFilm`,getFilmSerie)
    }
  }
  // data(){
  //   return {
  //     apiURL     : "https://api.themoviedb.org/3/search/movie/",
  //     apiURL2    : "https://api.themoviedb.org/3/search/tv/",
  //   }
  // },  
  //   methods:{
  //   getFilmSerie(select){
  //       axios.get(this.apiURL, {
  //         params : {
  //           api_key : "a39afba29712edaa4c2865fea35ce64f",
  //           query   : select
  //         }
  //       })
  //       .then((risposta) => {
  //         // handle success
  //         this.filmArray = risposta.data.results;
  //         this.select = ""
  //         console.log(this.filmArray)
  //       })
  //       .catch(function (error) {
  //           // handle error
  //           console.log(error);
  //       }),

  //       axios.get(this.apiURL2, {
  //         params : {
  //           api_key : "a39afba29712edaa4c2865fea35ce64f",
  //           query   : select
  //         }
  //       })
  //       .then((risposta2) => {
  //         // handle success
  //         this.serieArray = risposta2.data.results;
  //         this.select = ""

  //         console.log(this.serieArray)
  //       })
  //       .catch(function (error) {
  //           // handle error
  //           console.log(error);
  //       })
  //   }
  // }
} 
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.container-movies{
  background-color: rgb(79, 159, 161);
  position: fixed;
  width: 100%;
  top: 0;
  z-index: 10;

}

</style>
