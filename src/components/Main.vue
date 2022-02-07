<template>
  <div class="container">
    <div class="container-all">
      <h2>FILM</h2>
      <div class="film">
        <div v-for="movies in listFilms" 
          :key="movies.id">
            <Films
            :info="movies"
            />
        </div>
      </div>
      <div>
        <h2>SERIE TV</h2>
        <div class="serie">
          <div v-for="series in listSeries" 
            :key="series.id">
              <Series
              :cube="series"
              />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import Films from "./commons/Films.vue";
// import axios from "axios";
import Series from './commons/Series.vue';

export default {
  name       : "Main",
  components : {
    Films,
    Series
  },
  props : {
    listFilms  : Array,
    listSeries : Array
  },
  data(){
    return {
  //     apiURL     : "https://api.themoviedb.org/3/search/movie/",
  //     apiURL2    : "https://api.themoviedb.org/3/search/tv/",
      filmArray  : [],
      serieArray : []

    }
  },
  computed : {
    arrayFilmSerie(){
        return [...this.filmArray, ...this.serieArray]
    }
  }

  // methods:{
  //   getFilm(select){
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

h2{
  color: white;
  padding: 20px 100px;
}

.streak{
  background-color: rgb(71, 190, 155);
}

.film, .serie{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  padding: 10px 0;
}

.container-all{
  background-color: rgb(48, 48, 48);
  padding: 10px 0;
  margin: 66px 0;
}

h2{
 background-color: #202020;
 text-align: center;
 margin: 10px 0;
}

</style>