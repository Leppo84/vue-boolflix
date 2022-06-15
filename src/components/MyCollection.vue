<template>

</template>

<script>
import axios from "axios"


export default {
  name: 'MyCollection',
    components: {

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


  mounted(){
        setTimeout(()=> {
      this.collectionLoading=false;
    },2000);
  },
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

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

</style>

        apiUrl:`https://api.themoviedb.org/3/search/movie?api_key=351f43e41cbf21f7bd358651fcbab0d3&language=${lang}&query=${inputReq}&page=1&include_adult=true`, -->
