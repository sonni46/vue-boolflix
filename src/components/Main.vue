<template>
  <div class="main">
      <Movies :movies="movies"/>
      <Tv :tvs="tvs"/>
  </div>
</template>

<script>
import Movies from './Movies.vue'
import Tv from './Tv.vue'
export default {
    name:"Main",
    components : {
        Movies,
        Tv
    },
    props : ["movies","tvs"]
}
</script>


<style scoped lang="scss">
@import "@/style/General";
@import "@/style/Utilitis"; 

</style>