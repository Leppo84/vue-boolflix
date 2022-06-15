<template>

    <div class="container">
        <h2>FILM</h2>
        <div class="film-card" v-for="(film,index) in stampListFilms" :key="index">
            <img class="cover" :src="`http://image.tmdb.org/t/p/w500/${film.poster_path}`" :alt="film.title">
            <h3>{{film.title.toUpperCase()}}</h3>
            <h4>{{film.original_title}}</h4>
            <span>Lingua originale: {{film.original_language}}</span>
            <span>Voto: {{film.vote_average}}</span>
            <div class="star-vote">
                <!-- {{this.stars}} -->
                <!-- <font-awesome-icon icon="fa-solid fa-star"/> -->
                <!-- <font-awesome-icon icon="fas fa-star-half" /> -->
                <!-- <font-awesome-icon icon="fa-regular fa-star" /> -->

            </div>


        </div>
    </div>

</template>

<!-- https://countryflagsapi.com/png/br -->

<!-- `https://countryflagsapi.com/png/${Series.original_language}` -->

    <!-- {"backdrop_path":"/nWxgVgQubzlSmbjm7fbMIEeFTY4.jpg","first_air_date":"2001-10-02","genre_ids":[35],"id":4556,"name":"Scrubs","origin_country":["US"],"original_language":"en","original_name":"Scrubs","overview":"In the unreal world of Sacred Heart Hospital, John \"J.D.\" Dorian learns the ways of medicine, friendship and life.","popularity":80.314,"poster_path":"/u1z05trCA7AuSuDhi365grwdos1.jpg","vote_average":8,"vote_count":1167} -->

<!-- parto da un div vote; v-if non è vuoto il voto allora stampo il v-for; se è vuoto metto 5 stelline vuote; -->

<!-- prendo il voto da 1 a 10; lo divido per due; per ogni intero stampo una stella intera; per ogni parziale se il num è > 0,5 metto mezza stella, se il num è < di 0 stampo stella vuota; Se il num di stelline è < di 5 aggiungo le stelline mancanti. -->

<!-- per stampare una stellina ho un numero, con un ciclo lo faccio scendere di uno e appendo stellina...  -->

<script>

export default {
  name: 'FilmCard',
  props: {
    stampListFilms: Array, 
  },
//   data() {
//     return{      
//       stars: "0",
//     }
//   },
//   created () {
//     this.stampVoteFilm();
//   },
//   methods: {
//         stampVoteFilm(){
//         this.stars=parseFloat(this.film.vote_average);
//             console.log(stars);
//       return
//     },
//   }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

div.container {

    display: flex;
    flex-wrap: wrap;
    // justify-content: center;
    padding: 10px 0;
    background-color: #2e3a46;
    max-width: 100%;
    // max-height: calc(100vh - 60px);
    margin: 10px;

    h2 {
        margin: 6px 0 0;
        width: 100%;
        text-align: center;
        color: white;
    }

    div.film-card {
        display: flex;
        flex-direction: column;
        width: 16%;
        min-width: 100px;
        padding: 2px;
        margin: 2%;

        img.cover {
            max-width: 100%;
            max-height: auto;
            object-fit: cover;
            object-position: top center;
        }

        h3 {
            margin: 10px auto 2px;
            color: white;
            font-size: small;
        }

        h4 {
            margin: 0 auto 5px;
            color: grey;
            font-size: small;
        }
        span {
            color: grey;
            font-size: small;
        }

        img.flag {
            max-width: 10%;
        }
        .star-vote {
            color: rgb(255, 242, 0);
        }
    }
}



</style>