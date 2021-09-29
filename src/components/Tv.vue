<template>
  <div class="d-flex scroll ">
    <div class="col-2 mt-5 mx-5 my-3 flip-card" v-for="(tv,index) in tvs" :key="index">
       <div class="flip-card-inner">
          <div class="flip-card-front">
            <div v-if="tv.poster_path">
              <img :src="`https://image.tmdb.org/t/p/w300${tv.poster_path}`" alt="">
            </div>
            <div class="error" v-else>
              <img :src="require(`../assets/img/thumb.jpg`)" alt="">
            </div>
          </div>
          <div class="info bg-dark white ms-4 flip-card-back">
            <h3>{{tv.name}}</h3>
            <h4>{{tv.original_name}}</h4>
            <CountryFlag :country='language(tv.original_language)' size='normal'/>
            <div class="ms-2">
              <i v-for="(star,index) in starCounter " :key="index" class="fas fa-star" :class="calc(tv.vote_average,star)"></i>
            </div>
            <div class="overview">
              <h4>{{tv.overview}}</h4>
            </div>
          </div>
        </div>
    </div>
  </div>
</template>

<script>
import CountryFlag from 'vue-country-flag'
export default {
    name:"Tv",
    components : {
      CountryFlag
    },
    data(){
      return{
        starCounter: 5
      }
    },
    props:["tvs"],
    methods : {
      calc(info,i) {
        info = info / 2;
        Math.floor(info)
        console.log(info)
        console.log(i)
        if(i <= info){
          return 'yellow'
        }
        return false
      },
      language(e) {
         if(e == "en"){
          return "it"
      }
       return e
      }
    }
}
</script>

<style  scoped lang="scss">
.scroll {
    overflow: scroll;
    font-size: 20px;
}

.info {

  height: 450px;
      h3,
      h4 {
      margin-left: 10px;
      font-size:1rem;
      }
      .overview {
        width: 90%;
        height: 50%;
        overflow-y:scroll;
      }
      .overview::-webkit-scrollbar{
        width: 0;
        height: 0;
        background:transparent;
      }
}

.error {
  img{
    width: 100%;
    height: 450px;
    margin: auto;
  }
}

.white {
  color: white;
}

.scroll::-webkit-scrollbar {
  width: 0;
  height: 0;
  background:transparent;
}

.yellow {
  color: yellow;
}

.flip-card {
  background-color: transparent;
  width: 15%;
  height: 500px;
  perspective: 1000px; /* Remove this if you don't want the 3D effect */
}

/* This container is needed to position the front and back side */
.flip-card-inner {
  position: relative;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

/* Do an horizontal flip when you move the mouse over the flip box container */
.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}


.flip-card-front {
  img {
    width: 100%;
    margin: auto;
  }
  
}
/* Position the front and back side */
.flip-card-front, .flip-card-back {
  position: absolute;
  -webkit-backface-visibility: hidden; /* Safari */
  backface-visibility: hidden;
}

/* Style the front side (fallback if image is missing) */

/* Style the back side */
.flip-card-back {
  transform: rotateY(180deg);
}


</style>