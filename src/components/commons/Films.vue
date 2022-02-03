<template>
  <div>
    <div>
        <ul>
            <li>
                <p>Titolo           : {{info.title}}</p>
                <p>Titolo originale : {{info.original_title}}</p>
                <p>Lingua           : {{info.original_language}}</p>
                <p>Voto             : {{info.vote_average}}</p>
            </li>
        </ul>
    </div>
  </div>
</template>

<script>
export default {
    name : "Films",
    props : {
        info : Object
 }
}
</script>

<style>

</style>