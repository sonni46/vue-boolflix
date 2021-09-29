<template>
    <div class="scroll d-flex">
      <div class="col-2 mx-5 mt-4 flip-card " v-for="(movi,index) in movies" :key="index">
        <div class=" flip-card-inner">
          <div class="flip-card-front">
            <div v-if="movi.poster_path">
              <img :src="`https://image.tmdb.org/t/p/w300${movi.poster_path}`" alt="">
            </div>
            <div class="error" v-else>
              <img :src="require(`../assets/img/thumb.jpg`)" alt="">
            </div>
          </div>
          <div class="info bg-dark white ms-4 flip-card-back">
            <h3>{{movi.title}}</h3>
            <h4>{{movi.original_title}}</h4>
            <CountryFlag :country='movi.original_language' size='normal'/>
            <div class="ms-2">
              <i v-for="(star,index) in starCounter " :key="index" class="fas fa-star" :class="calc(movi.vote_average,star)"></i>
            </div>
            <div class="overview">
              <h4>{{movi.overview}}</h4>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>
<script>
import CountryFlag from 'vue-country-flag'
export default {
    name : 'Movies',
    components :{
      CountryFlag
    },
    props : ["movies"],
    data() {
      return{
         starCounter: 5
      }
    },
    methods: {
      calc(info,i) {
        info = info / 2;
        Math.floor(info)
        console.log(info)
        if(i <= info){
          return 'yellow'
        }
        return false
      },
    },
}
</script>

<style scoped lang="scss">
@import "@/style/General";
@import "@/style/Utilitis";  

.scroll {
    overflow: scroll;
    font-size: 20px;
}

.info {
  // flex-basis:auto;
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

.white {
  color: white;
}

.yellow {
  color: yellow;
}

.scroll::-webkit-scrollbar {
  width: 0;
  height: 0;
  background:transparent;
}

.flip-card {
  background-color: transparent;
  width: 15%;
  height: 500px;
  // perspective: 1000px; /* Remove this if you don't want the 3D effect */
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