<template>
  <div id="app">
    <HeaderMenu/>
    <main class="container">   
      <font-awesome-icon icon="user-secret" />
      
      <LoadingSplash v-if="collectionLoading"/>
      <FilmCard v-else :stampListFilms="listFilms"/>
      <SeriesCard :stampListSeries="listSeries"/>

    </main>
  </div>
</template>

<script>
import HeaderMenu from './components/HeaderMenu.vue'
import LoadingSplash from "./components/LoadingSplash.vue";
import FilmCard from "./components/FilmCard.vue"
import SeriesCard from "./components/SeriesCard.vue"
import axios from "axios"


export default {
  name: 'App',
  components: {
    HeaderMenu,
    LoadingSplash,
    FilmCard,
    SeriesCard,
  },
    data(){
    return{      
      collectionLoading : true,
      inputLang : "it-IT",
      inputReq : "fight",
      filmUrl : "",
      seriesUrl : "",


      listFilms: [],
      listSeries: [],
    }
  },
    created(){
    this.createFilmList();
    this.createSeriesList();

  },
    methods: {
    createUrlFilms(){
      this.filmUrl = "https://api.themoviedb.org/3/search/movie?api_key=351f43e41cbf21f7bd358651fcbab0d3&language=" + this.inputLang + "&query=" + this.inputReq + "&page=1&include_adult=true";
      return
    },
    createFilmList(){ 
      this.createUrlFilms();
      axios
        .get(this.filmUrl)
        .then(apiLog => {
          this.listFilms = apiLog.data.results;
            console.log(this.listFilms);
        })
        .catch((error) => {
            console.log("errore", error);
        })
    },
        createUrlSeries(){
      this.seriesUrl = "https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=" + this.inputLang + "&query=" + this.inputReq;
      return
    },
        createSeriesList(){ 
      this.createUrlSeries();
      axios
        .get(this.seriesUrl)
        .then(apiSeriesLog => {
          this.listSeries = apiSeriesLog.data.results;
            console.log(this.listSeries);
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
