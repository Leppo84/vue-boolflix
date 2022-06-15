<template>
  <div id="app">
    <HeaderMenu/>
    <main class="container">   
    <LoadingSplash v-if="collectionLoading"/>
    <filmCard v-else :stampList="listFilms"/>
    </main>
  </div>
</template>

<script>
import HeaderMenu from './components/HeaderMenu.vue'
import filmCard from "./filmCard.vue"
import LoadingSplash from "./LoadingSplash.vue";
import axios from "axios"


export default {
  name: 'App',
  components: {
    HeaderMenu,
    LoadingSplash,
    filmCard,
  },
    data(){
    return{      
      collectionLoading : true,
      inputLang : "it-IT",
      inputReq : "a",
      apiUrl : "",

      listFilms: [],
    }
  },
    created(){
    this.createFilmList();
  },
    methods: {
    createUrl(){
      this.apiUrl = "https://api.themoviedb.org/3/search/movie?api_key=351f43e41cbf21f7bd358651fcbab0d3&language=" + this.inputLang + "&query=" + this.inputReq + "&page=1&include_adult=true";
      return
    },
    createFilmList(){ 
      this.createUrl();
      axios
        .get(this.apiUrl)
        .then(apiLog => {
          this.listFilms = apiLog.data.results;
            console.log(this.listFilms);
        })
        .catch((error) => {
            console.log("errore", error);
        })
    },
  },
  // computed: {
  //     filteredAlbums() {
  //         if( this.myGenre === "All"){
  //           console.log(this.myGenre);
  //         return this.callAlbums;
  //         }
  //         else {
  //           console.log(this.myGenre);
  //                     return this.callAlbums.filter(item=> {
  //                       return item.genre.includes(this.myGenre);
  //         });
  //       }
  //     }
  //   },
    mounted(){
        setTimeout(()=> {
      this.collectionLoading=false;
    },2000);
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

  div.container {
    display: flex;
    flex-wrap: wrap;
    // justify-content: center;
    padding: 20px;
    // max-width: 60%;
    // max-height: calc(100vh - 60px);
    margin: 0 auto;
    // overflow: auto;
}
}

#app {
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
}

</style>
