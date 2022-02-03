<template>
<div>
    <div class="container-file serie">
        <ul>
            <li class="tv">
                <div class="w_50">
                    <img 
                    class="copertina"
                    :src= "getImage()" alt="">
                </div>
                <div>
                    <h3>Titolo           : {{cube.name}}</h3>
                    <h5>Titolo originale : {{cube.original_name}}</h5>
                    <p class="lingua">Lingua
                    <img 
                    class="img_flag"
                    :src="getFlags2()">
                    </p>
                    <p>Voto             : {{cube.vote_average}}</p> 
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
            }    
        }

    }
}

</script>

<style scoped lang="scss">

.serie{
    background-color: rgb(136, 187, 59);
    display: flex;
}

.lingua{
    display: inline-block;

    .img_flag{
    margin: 0 10px;
    height: 15px;
    }
}


</style>