<template>
<div>
    <div class="container-file serie">
        <ul>
            <li class="tv">
                <div class="w_img">
                    <img 
                    class="copertina"
                    :src= "getImage()" alt="">
                </div>
                <div class="descrizione">
                    <h3>Titolo           : {{cube.name}}</h3>
                    <h5>Titolo originale : {{cube.original_name}}</h5>
                    <p class="lingua">Lingua
                    <img 
                    class="img_flag"
                    :src="getFlags2()">
                    </p>
                    <p
                    v-if="getNumber() != 0" >Voto             : {{getStars()}} </p>
                    <p v-else >  Voto : Senza voto </p>
                </div>
            </li>
        </ul>
    </div>
</div>
</template>

<script>
export default {
    name  : "Series",
    props : {
        cube : Object
    },
    // data(){
    //     return{
    //         star : 0
    //     }
    // },
    methods : {
        getFlags2(){
            if (this.cube.original_language == "en"){
                return "https://static-cdn.whokeys.com/mall/image/region/Great_Britain.png"
            } else if (this.cube.original_language == "it"){
                return "https://static-cdn.whokeys.com/mall/image/region/Italy.png"
            } else {
                return "https://static-cdn.whokeys.com/mall/image/region/Worldwide.png"
            }
        },
        getImage(){
            if (!this.cube.poster_path == ""){
                return "https://image.tmdb.org/t/p/w342/" + this.cube.poster_path
            } else {
                return "https://repository-images.githubusercontent.com/279611541/b7e1e580-c611-11ea-9b24-523c65baea0e"
            } 
        },
        getNumber(){
            return (this.cube.vote_average / 2).toFixed(0)
        },
        getStars(){
            let stelle = "" 
            let numero = this.getNumber()
                for(let i=0; i < numero; i++){
                    stelle += "★"
                }
                return stelle
        }
    }
}

</script>

<style scoped lang="scss">

</style>