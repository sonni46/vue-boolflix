<template>
  <div class="d-flex mt-5 scroll">
      <div class="col-2" v-for="(tv,index) in tvs" :key="index">
        <!-- <img :src="`https://image.tmdb.org/t/p/w300${movi.poster_path}`" alt=""> -->
        <div class="info bg-dark white ms-4">
          <h3>{{tv.name}}</h3>
          <h4>{{tv.original_name}}</h4>
          <CountryFlag :country='tv.original_language' size='normal'/>
          <h4>{{tv.vote_average}}</h4>
          <div class="overview">
            <h4>{{tv.overview}}</h4>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
export default {
    name:"Tv",
    props:["tvs"],

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
</style>