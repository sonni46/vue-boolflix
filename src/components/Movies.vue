<template>
  <div class="d-flex mt-5 scroll">
      <div class="col-2" v-for="(movi,index) in movies" :key="index">
        <!-- <img :src="`https://image.tmdb.org/t/p/w300${movi.poster_path}`" alt=""> -->
        <div class="info bg-dark white ms-4">
          <h3>{{movi.title}}</h3>
          <h4>{{movi.original_title}}</h4>
          <h4>{{movi.original_language}}</h4>
          <h4>{{movi.vote_average}}</h4>
          <div class="overview">
            <h4>{{movi.overview}}</h4>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
export default {
    name : 'Movies',
    props : ["movies"],
    data() {

    },
    methods: {

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
      font-size:1vw;
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