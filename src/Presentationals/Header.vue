<template>
  <div class="wrapper">
    <Nav />
    <h1>Rick and Morty</h1>
    <img src="../assets/ricky&morty_banner.png" width="800" alt="banner" />
  </div>
</template>

<script>
import Nav from "../Presentationals/Nav.vue";
export default {
  name: "Header",
  components: {
    Nav,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  font-size: 50px;
  margin-top: 0;
  margin-bottom: 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
</style>
