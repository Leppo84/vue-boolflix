<template>
    <div class="container">
        <h2>FILM</h2>
        <div class="film-card" v-for="(film,index) in stampListFilms" :key="index">
            <img class="cover" :src="`http://image.tmdb.org/t/p/w500/${film.poster_path}`" :alt="film.title">
            <!-- <img src="../assets/en.svg" alt=""> -->
            <h3>{{film.title.toUpperCase()}}</h3>
            <h4>{{film.original_title}}</h4>
            <span>Lingua: {{film.original_language}} <img class="flag" :src="stampFlag(film.original_language)"></span>

            <div class="empty" v-if="film.vote_average===0">Il film non ha voti</div>
            <div class="star-vote" v-else>
                <span>Voto: </span>
                <font-awesome-icon icon="fa-solid fa-star" v-for="(stars, i) in stampStars(film.vote_average)" :key="i"/>
                <font-awesome-icon v-if="stampHalfStar(film.vote_average) === true" icon="fa-solid fa-star-half-stroke" />
                <font-awesome-icon icon="fa-regular fa-star" v-for="(noStars, j) in stampEmptyStars(film.vote_average)" :key="j"/>
            </div>
        </div>
    </div>
</template>

    <!-- {"backdrop_path":"/nWxgVgQubzlSmbjm7fbMIEeFTY4.jpg","first_air_date":"2001-10-02","genre_ids":[35],"id":4556,"name":"Scrubs","origin_country":["US"],"original_language":"en","original_name":"Scrubs","overview":"In the unreal world of Sacred Heart Hospital, John \"J.D.\" Dorian learns the ways of medicine, friendship and life.","popularity":80.314,"poster_path":"/u1z05trCA7AuSuDhi365grwdos1.jpg","vote_average":8,"vote_count":1167} -->

<!-- se il num di stelline è < di 5 aggiungo le stelline mancanti (? vedo se mi avanza tempo). -->

<script>

export default {
  name: 'FilmsCard',
  props: {
    stampListFilms: Array, 
  },
  methods: {
        stampStars(rawVoteStars){
            // rawVoteStars = parseInt.Math.floor(rawVoteStars/2);
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

// var quotient = Math.floor(y/x);
// var remainder = y % x;

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
            width: 20px;
        }
        .star-vote {
            color: rgb(255, 242, 0);
            margin: 2px;
        }

        .empty {
            margin: 2px;
        }
    }
}



</style>