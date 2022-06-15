<template>
    <header>
        <span class="logo">BOOTFLIX</span>
        <div class="search-films">
            <span>Cerca...</span>
                <input type="text" v-model="inputTxt" @keyup="$emit('callSearch',inputTxt)">
                <button @click="$emit('callSearch',inputTxt)">Cerca</button>
        </div>
    </header>
</template>

<script>

export default {
  name: 'HeaderMenu',
  data(){
    return{
        inputTxt: "",
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

header {
    width: 100%;
    height: 60px;
    background-color: black;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: center;

    .logo {
        display: inline-block;
        width: 60px;
        padding: 8px;
        margin: 0 16px;
        color: red;
    }

    div.search-films {
        padding: 8px;
        margin: 0 16px;
        color: white;


        span {
            display: inline-block;
            color: white;
            margin-right: 16px;
        }
        select {
            width: 150px;
        }

        button {
            margin: 5px;
        }

    }
}

</style>

