<template>
  <div class="main">
      <movies :movies="movies"/>
  </div>
</template>

<script>
import Movies from './Movies.vue'
export default {
    name:"Main",
    computed : {
        Movies
    },
    props : ["movies"]

}
</script>


<style>
@import "@/style/General";
@import "@/style/Utilitis";

</style>