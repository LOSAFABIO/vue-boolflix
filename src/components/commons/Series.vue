<template>
<div>
    <div>
        <ul>
            <li >
                <p>Titolo           : {{cube.name}}</p>
                <p>Titolo originale : {{cube.original_name}}</p>
                <p class="lingua">Lingua
                <img 
                class="img_flag"
                :src="getFlags2()">
                </p>
                <p>Voto             : {{cube.vote_average}}</p>
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

</style>