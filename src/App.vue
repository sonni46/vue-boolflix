<template>
  <div id="app">
    <Header @serching="getSerch" />
  </div>
</template>

<script>
// const axios = require('axios').default;
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Header
  },
  data() {
    return{
      apiUrl:"https://api.themoviedb.org/3/search/movie",
      key:"?api_key=6ba885185de008c100b93e59c3a6c22b",
      query:"&query=",
      sercher:""
    }
  },
  created(){
    // getMovi()
  },
  methods: {
    getSerch (info) {
      this.sercher = info
    }


  //   getMovi(){
  //   axios.get(this.apiUrl + this.key + this.query + this.sercher)
  //   .thet(el => {
  //     console.log(el)
  //   })
  // }
  }
}
</script>

<style lang="scss">

</style>
