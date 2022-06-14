<template>
    <div class="container">
        <div class="film-card" v-for="(film,index) in stampList" :key="index">
            <img :src="`http://image.tmdb.org/t/p/w500/${film.backdrop_path}`" :alt="film.title">
            <h4>
                {{film.title.toUpperCase()}}
            </h4>
            <h3>{{film.original_title}}</h3>
            <span>Lingua originale: {{film.original_language}}</span>
            <span>Voto: {{film.vote_average}}</span>
        </div>
    </div>
</template>

<script>

export default {
  name: 'filmCard',
  props: {
    stampList: Array, 
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.container {
    display: flex;
    flex-wrap: wrap;
    // justify-content: center;
    padding: 10px 0;
    background-color: #2e3a46;
    max-width: 100%;
    // max-height: calc(100vh - 60px);
    margin: 10px;
    div.film-card {
        display: flex;
        flex-direction: column;
        width: 16%;
        min-width: 100px;
        padding: 12px;
        margin: 2%;

        img {
            max-width: 100%;
            max-height: 150px;
            object-fit: cover;
            object-position: top center;

        }

        h4 {
            margin: 10px auto;
            color: white;
            font-size: small;
        }
        span {
            color: grey;
            font-size: small;
        }
    }
}

</style>
