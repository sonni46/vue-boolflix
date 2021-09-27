<template>
  <div class="d-flex mt-5 scroll">
      <div class="col-2" v-for="(movi,index) in movies" :key="index">
        <!-- <img :src="`https://image.tmdb.org/t/p/w300${movi.poster_path}`" alt=""> -->
        <div class="info bg-dark white ms-4">
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

.yellow {
  color: yellow;
}

.scroll::-webkit-scrollbar {
  width: 0;
  height: 0;
  background:transparent;
}
</style>