<template>
  <div class="container">
    <div class="streak">
      <Cerca @filtra="getFilm"/>
    </div>
  </div>
</template>

<script>

import Cerca from "./commons/Cerca.vue";
import axios from "axios";

export default {
  name       : "Main",
  components : {
    Cerca
  },
  data(){
    return {
      apiURL    : "https://api.themoviedb.org/3/search/movie/",
      filmArray : [],
    }
  },
  methods:{
    getFilm(select){
        axios.get(this.apiURL, {
          params : {
            api_key : "a39afba29712edaa4c2865fea35ce64f",
            query   : select
          }
        })
        .then((risposta) => {
          // handle success
          this.filmArray = risposta.data.results;
          console.log(this.filmArray)
        })
        .catch(function (error) {
            // handle error
            console.log(error);
        })

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.streak{
  background-color: cadetblue;
}


</style>
