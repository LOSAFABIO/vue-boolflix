<template>
<div>
  <div>
    <input 
    class="cerca" 
    type="text" 
    placeholder="Cerca quello che più ti interessa!"
    v-model.trim="select" 
    @keyUp="$emit(`filtraEnter`, select)">

    <button 
    @click.prevent="$emit(`filtra`, select)" 
    type="button">
    Clicca qui!
    </button>
  </div>
</div>
</template>

<script>
export default {
    name: "Cerca",
    data(){
        return{
            select : ""
        }
    },
}
</script>

<style scoped lang="scss">

.cerca{
    width: 220px;
    margin: 20px;
    border: none;
    border-radius: 10px;
    padding: 5px 5px;
}

button{
    padding: 3px 15px;
}

</style>