<template>
  <div id="app">
    <HeaderMenu/>
    <main>
      <MyCollection/>
    </main>
  </div>
</template>

<script>
import HeaderMenu from './components/HeaderMenu.vue'
import MyCollection from './components/MyCollection.vue'


export default {
  name: 'App',
  components: {
    HeaderMenu,
    MyCollection,
  },
}

</script>

<style lang="scss">
* {
  margin: 0;
  border: 0;
  box-sizing: border-box;
}

main {
  background-color: #1e2d3b;
  text-align: center;
  width: 100%;
  height: calc(100vh - 60px);
  overflow: auto;
}

#app {
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
}

</style>
