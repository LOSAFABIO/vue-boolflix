<template>
  <div class="container">
    <div class="streak">
        <Cerca 
        @filtra="getFilm"
        @filtraEnter="getFilm"
        />
    </div>
    <div class="container-all">
      <div v-for="(movies,indice) in filmArray" 
        :key="indice">
          <Films
          :info="movies"
          />
      </div>
      <div v-for="(series,indice) in serieArray" 
        :key="indice">
          <Series
          :cube="series"
          />
      </div>
    </div>
  </div>
</template>

<script>

import Films from "./commons/Films.vue";
import Cerca from "./commons/Cerca.vue";
import axios from "axios";
import Series from './commons/Series.vue';

export default {
  name       : "Main",
  components : {
    Cerca,
    Films,
    Series
  },
  data(){
    return {
      apiURL     : "https://api.themoviedb.org/3/search/movie/",
      apiURL2    : "https://api.themoviedb.org/3/search/tv/",
      filmArray  : [],
      serieArray : []

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
        }),

        axios.get(this.apiURL2, {
          params : {
            api_key : "a39afba29712edaa4c2865fea35ce64f",
            query   : select
          }
        })
        .then((risposta2) => {
          // handle success
          this.serieArray = risposta2.data.results;
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.streak{
  background-color: cadetblue;
}

.container-all{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

</style>