<template>
  <div class="col-12 d-flex bg-dark">
    <div class="col-10">
      <h2 class="myRed ps-2">BOOLFLIX</h2>
    </div>
    <div class="pt-2 w-100">
      <input v-model="search" @keyup.enter="$emit('serching',search)" type="text" placeholder="Search" class="me-1 px-2">
      <button class="button px-2 background-c-red" @click="$emit('serching',search)">Search</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
    search:"",
    }
  },
  created() {
    this.reset ()
  } ,
  methods : {
    reset () {
      this.$emit("serching",this.search)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "@/style/General";
@import "@/style/Utilitis";

.myRed {
  color: rgb(168, 5, 5);
  
}
.background-c-red {
  background-color: rgb(168, 5, 5)
}
.button {
  color: white;
  outline: none;
  border: none;
}


</style>
