<template>

    <div class="container">
        <h2>SERIES</h2>
        <div class="film-card" v-for="(series,index) in stampListSeries" :key="index">
            <img :src="`http://image.tmdb.org/t/p/w500/${series.poster_path}`" :alt="series.title">
            <h3>{{series.name.toUpperCase()}}</h3>
            <h4>{{series.original_name}}</h4>
            <span>Lingua originale: {{series.original_language}}</span>
            <span>Voto: {{series.vote_average}}</span>
        </div>
    </div>

</template>

<script>

export default {
  name: 'SeriesCard',
  props: {
    stampListSeries: Array, 
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

        img {
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
    }
}

</style>
