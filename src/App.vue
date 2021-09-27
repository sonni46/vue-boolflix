<template>
  <div id="app" class="container-fluid px-0">
    <Header @serching="getSerch" />
    <div class="">
      <Main :movies="movies" :tvs="tvs"/>
    </div>
  </div>
</template>

<script>
const axios = require('axios').default;
import Header from './components/Header.vue';
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data() {
    return{
      apiUrl:"https://api.themoviedb.org/3/search/",
      key:"?api_key=6ba885185de008c100b93e59c3a6c22b",
      query:"&query=",
      sercher:"",
      apiMovie : "movie",
      apiTv : "tv",
      movies : [],
      tvs : []

    }
  },
  created(){
    this.getMovi()
  },
  methods: {
    getSerch (info) {
      this.sercher = info;
      this.getMovi();
      this.getTv();
    },
    getMovi(){
      axios.get(this.apiUrl + this.apiMovie + this.key + this.query + this.sercher)
      .then(el => {
        console.log(el.data.results)
      this.movies = el.data.results
    })
  },
  getTv(){
    axios.get(this.apiUrl + this.apiTv + this.key + this.query + this.sercher)
      .then(Element => {
        console.log(Element.data.results)
      this.tvs = Element.data.results
    })
  }
  }
}
</script>

<style lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.min.css';
@import "@/style/General";
@import "@/style/Utilitis";

</style>
