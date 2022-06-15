<template>

    <div class="container">
        <h2>SERIES</h2>
        <div class="film-card" v-for="(series,index) in stampListSeries" :key="index">
            <img :src="`http://image.tmdb.org/t/p/w500/${series.backdrop_path}`" :alt="series.title">
            <h3>{{series.name.toUpperCase()}}</h3>
            <h4>{{series.original_name}}</h4>
            <span>Lingua originale: {{series.original_language}}</span>
            <span>Voto: {{series.vote_average}}</span>
        </div>
    </div>

    <!-- <img
  src="https://flagcdn.com/16x12/za.png"
  srcset="https://flagcdn.com/32x24/za.png 2x,
    https://flagcdn.com/48x36/za.png 3x"
  width="16"
  height="12"
  alt="South Africa"> -->

<!-- https://countryflagsapi.com/png/br -->

<!-- `https://countryflagsapi.com/png/${Series.original_language}` -->

    <!-- {"backdrop_path":"/nWxgVgQubzlSmbjm7fbMIEeFTY4.jpg","first_air_date":"2001-10-02","genre_ids":[35],"id":4556,"name":"Scrubs","origin_country":["US"],"original_language":"en","original_name":"Scrubs","overview":"In the unreal world of Sacred Heart Hospital, John \"J.D.\" Dorian learns the ways of medicine, friendship and life.","popularity":80.314,"poster_path":"/u1z05trCA7AuSuDhi365grwdos1.jpg","vote_average":8,"vote_count":1167} -->

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
    }
}

</style>
