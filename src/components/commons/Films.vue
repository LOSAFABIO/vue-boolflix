<template>
  <div>
    <div class="container-file film">
        <ul>
            <li class="tv">
                <div class="w_50">
                    <img 
                    class="copertina"
                    :src= "getImage()" alt="">
                </div>
                <div>
                    <h3>Titolo           : {{info.title}}</h3>
                    <h5>Titolo originale : {{info.original_title}}</h5>
                    <p class="lingua">Lingua
                    <img 
                    class="img_flag"
                    :src="getFlags()">
                    </p>
                    <p>Voto             : {{getStars()}}</p>
                </div>
            </li>
        </ul>
    </div>
  </div>
</template>

<script>
export default {
    name  : "Films",
    props : {
        info  : Object
    },

    methods : {
        getFlags(){
            if (this.info.original_language == "en"){
                return "https://static-cdn.whokeys.com/mall/image/region/Great_Britain.png"
            } else if (this.info.original_language == "it"){
                return "https://static-cdn.whokeys.com/mall/image/region/Italy.png"
            } else {
                return "https://static-cdn.whokeys.com/mall/image/region/Worldwide.png"
            }
        },
        getImage(){
            if (!this.info.poster_path == ""){
                return "https://image.tmdb.org/t/p/w342/" + this.info.poster_path
            }
        },
        getNumber(){
            return (this.info.vote_average / 2).toFixed(0)
        },
        getStars(){
            let stelle = "" 
            let numero = this.getNumber()
            
            for(let i=0; i < numero; i++){
                stelle += `★`
            }
            return stelle
        }

    }
}
</script>

<style scoped lang="scss">

.lingua{
    display: inline-block;

    .img_flag{
    margin: 0 10px;
    height: 15px;
    }
}

.film{
    background-color: rgb(209, 132, 69);
    display: flex;
}

</style>