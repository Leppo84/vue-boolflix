<template>

    <div class="container">
        <h2>FILM</h2>
        <div class="film-card" v-for="(film,index) in stampListFilms" :key="index">
            <img class="cover" :src="`http://image.tmdb.org/t/p/w500/${film.backdrop_path}`" :alt="film.title">
            <h3>{{film.title.toUpperCase()}}</h3>
            <h4>{{film.original_title}}</h4>
            <span>Lingua originale: {{film.original_language}}</span>
            <span>Voto: {{film.vote_average}}</span>
        </div>
    </div>

</template>

<script>

export default {
  name: 'FilmCard',
  props: {
    stampListFilms: Array, 
  },
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
            max-height: 150px;
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
    }
}



</style>