<template>
  <div id="app" class="container-fluid px-0">
    <Header @serching="getSerch" />
    <div class="">
      <Main :movies="movies"/>
    </div>
  </div>
</template>

<script>
const axios = require('axios').default;
import Header from './components/Header.vue';
import Main from './components/Movies.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data() {
    return{
      apiUrl:"https://api.themoviedb.org/3/search/movie",
      key:"?api_key=6ba885185de008c100b93e59c3a6c22b",
      query:"&query=",
      sercher:"",
      movies : []
    }
  },
  created(){
    this.getMovi()
  },
  methods: {
    getSerch (info) {
      this.sercher = info;
      this.getMovi();
    },
    getMovi(){
      axios.get(this.apiUrl + this.key + this.query + this.sercher)
      .then(el => {
        console.log(el.data.results)
      this.movies = el.data.results
    })
  }
  }
}
</script>

<style lang="scss">
@import "@/style/General";
@import "@/style/Utilitis";

</style>
