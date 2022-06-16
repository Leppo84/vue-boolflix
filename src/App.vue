<template>
  <div id="app">
    <HeaderMenu @callSearch="createFilmList"/>
    <main class="container">         
      <LoadingSplash v-if="collectionLoading"/>
      <div v-else>
        <FilmsCard :stampListFilms="listFilms"/>
        <SeriesCard :stampListSeries="listSeries"/>
      </div>

    </main>
  </div>
</template>

<script>
import HeaderMenu from './components/HeaderMenu.vue'
import LoadingSplash from "./components/LoadingSplash.vue";
import FilmsCard from "./components/FilmsCard.vue"
import SeriesCard from "./components/SeriesCard.vue"
import axios from "axios"


export default {
  name: 'App',
  components: {
    HeaderMenu,
    LoadingSplash,
    FilmsCard,
    SeriesCard,
  },
    data(){
    return{      
      collectionLoading : true,
      inputLang : "it-IT",
      // inputReq : "Ciao",
      filmUrl : "",
      seriesUrl : "",
      listFilms: [],
      listSeries: [],
    }
  },
    created(){
    this.createFilmList("benvenuto");
    this.createSeriesList("benvenuto");

  },
    methods: {
    createUrlFilms(inputTxt){
      this.filmUrl = "https://api.themoviedb.org/3/search/movie?api_key=351f43e41cbf21f7bd358651fcbab0d3&language=" + this.inputLang + "&query=" + inputTxt + "&page=1&include_adult=true";
      return
    },
    createFilmList(inputTxt){ 
      this.createUrlFilms(inputTxt);
      axios
        .get(this.filmUrl)
        .then(apiLog => {
          this.listFilms = apiLog.data.results.splice(0,15);
            // console.log(this.listFilms);
          this.createSeriesList(inputTxt)
        })
        .catch((error) => {
            console.log("errore", error);
        })
    },
        createUrlSeries(inputTxt){
      this.seriesUrl = "https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=" + this.inputLang + "&query=" + inputTxt + "&include_adult=true";
      return
    },
        createSeriesList(inputTxt){ 
      this.createUrlSeries(inputTxt);
      axios
        .get(this.seriesUrl)
        .then(apiSeriesLog => {
          this.listSeries = apiSeriesLog.data.results.splice(0,15);
            // console.log(this.listSeries);
        })
        .catch((error) => {
            console.log("errore", error);
        })
    },
  },
    mounted(){
        setTimeout(()=> {
      this.collectionLoading=false;
    },1000);
  },
}

</script>

<style lang="scss">

* {
  margin: 0;
  border: 0;
  box-sizing: border-box;
}

#app {
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
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

</style>
