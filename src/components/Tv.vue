<template>
  <div class="d-flex mt-5 scroll">
      <div class="col-2" v-for="(tv,index) in tvs" :key="index">
        <!-- <img :src="`https://image.tmdb.org/t/p/w300${tv.poster_path}`" alt=""> -->
        <div class="info bg-dark white ms-4">
          <h3>{{tv.name}}</h3>
          <h4>{{tv.original_name}}</h4>
          <CountryFlag :country='tv.original_language' size='normal'/>
          <div class="ms-2">
            <i v-for="(star,index) in starCounter " :key="index" class="fas fa-star" :class="calc(tv.vote_average,star)"></i>
          </div>
          <div class="overview">
            <h4>{{tv.overview}}</h4>
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
  // flex-basis:auto;
  height: 342px;
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

.scroll::-webkit-scrollbar {
  width: 0;
  height: 0;
  background:transparent;
}

.yellow {
  color: yellow;
}
</style>