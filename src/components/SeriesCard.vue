<template>

    <div class="container">
        <h2>SERIES</h2>
        <div class="film-card" v-for="(series,index) in stampListSeries" :key="index">
            <img class="cover" :src="`http://image.tmdb.org/t/p/w500/${series.poster_path}`" :alt="series.title">
            <div class="info">
                <h3>{{series.name.toUpperCase()}}</h3>
                <h4>{{series.original_name}}</h4>
                <div class="lang">
                    <b>Lingua: </b>
                    <img class="flag" :src="stampFlag(series.original_language)">
                    <span> ( {{series.original_language}} )</span>
                </div>
                <div class="empty" v-if="series.vote_average===0">Questa serie non è stata ancora votata</div>
                <div class="star-vote" v-else>
                    <span><b> Voto: </b>{{series.vote_average}}</span>
                    <br>
                    <font-awesome-icon icon="fa-solid fa-star" v-for="(stars, i) in stampStars(series.vote_average)" :key="i"/>
                    <font-awesome-icon v-if="stampHalfStar(series.vote_average) === true" icon="fa-solid fa-star-half-stroke" />
                    <font-awesome-icon icon="fa-regular fa-star" v-for="(noStars, j) in stampEmptyStars(series.vote_average)" :key="j"/>
                </div>
                <p class="overview" ><b>Panoramica:</b> {{series.overview.slice(0,140)}}...</p>
            </div>
        </div>
    </div>
</template>

<script>

export default {
  name: 'SeriesCard',
  props: {
    stampListSeries: Array, 
  },
    methods: {
        stampStars(rawVoteStars){
                let halved = Math.floor(rawVoteStars/2);
                return halved
        },
        stampHalfStar(rawVoteHalf){
            if (rawVoteHalf === 0) {
                return false;           
            }
            else {
                let halved =rawVoteHalf/2;
                let decimal = halved % 1;
                if (decimal > 0) {
                    return true;           
                }
                else {
                    return false;           
                }
            }
        },
        stampEmptyStars(rawVoteEmpty){
                let halved =rawVoteEmpty/2;
                let empty = 5 - (Math.ceil(halved));
                return empty;
            },
        stampFlag(code) {
            if (code == "en") {
                return code="https://upload.wikimedia.org/wikipedia/en/a/ae/Flag_of_the_United_Kingdom.svg";

                }
            else if (code == "it"){
                return code="https://upload.wikimedia.org/wikipedia/commons/c/ca/Bandiera_italiana_foto.svg";

            } 
            else if (code == "de"){
                return code="https://upload.wikimedia.org/wikipedia/commons/b/ba/Flag_of_Germany.svg";

            } 
            else if (code == "es"){
                return code="https://upload.wikimedia.org/wikipedia/commons/9/9a/Flag_of_Spain.svg";
            }
  
            else {
             return code="https://upload.wikimedia.org/wikipedia/commons/thumb/4/48/Gay_Pride_Flag.svg/1024px-Gay_Pride_Flag.svg.png";
            }
        },
  }
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
        min-height: 200px;
        padding: 2px;
        margin: 2%;
        border: 1px solid white;
            img.cover {
                width: auto;
                height: 300px; 
                object-fit: cover;
                object-position: top center;
            }
            div.info {
                display: none;
            }
        }
    div.film-card:hover {
        background-color: rgba($color: #000000, $alpha: 0.4);
        img.cover {
            display: none;
        }
        div.info {
            text-align: start;
            display: flex;
            flex-direction: column;
            padding: 10px;
            color: grey;
            font-size: small;
            line-height: 1.2rem;

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
                    position: relative;
                    top: 2px;
                    width: 20px;
                }
                .star-vote {
                    color: rgb(255, 242, 0);
                    margin: 6px 0;
                    
                }
        } 
    }
}

</style>
