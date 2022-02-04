<template>
<div class="container-header">
    <div class="container-logo">
        <h1>boolflix</h1>
    </div>
    <div class="container-btn">
        <input 
        class="cerca" 
        type="text" 
        placeholder="Cerca quello che più ti interessa!"
        v-model.trim="select">
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
            select : "",
        }
    }
}
</script>

<style scoped lang="scss">

.container-btn{
    text-align: end;
}

.container-logo{
        display: inline-block;

        h1{
            text-transform: uppercase;
            color: rgb(177, 43, 43);
        }
}

.cerca{
    width: 220px;
    margin: 20px;
    border: none;
    border-radius: 10px;
    padding: 5px 5px;
}

.container-header{
  display: flex;
  justify-content: space-between;
  align-items: center;  
  padding: 0 20px;

}


button{
    padding: 3px 15px;
}

</style>