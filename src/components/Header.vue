<template>
  <div>
    <input v-model="search" @keyup="$emit('serching',search)" type="text" placeholder="Search">
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
  methods : {
    // getSerch () {
    //   this.search = "";
    //   this.$emit("serching",this.search)
    // }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
