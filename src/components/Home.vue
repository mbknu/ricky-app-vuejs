<template>
  <div class="wrapper">
    <Header />
    <div class="container"></div>
    <Footer />
  </div>
</template>

<script>
import axios from "axios";
import Header from "../Presentationals/Header.vue";
import Footer from "../Presentationals/Footer.vue";

export default {
  name: "Home",
  components: {
    Header,
    Footer,
  },
  created() {
    axios
      .get("https://rickandmortyapi.com/api/character")
      .then((response) => response.data)
      .catch((error) => {
        this.errorMessage = error.message;
        console.error("There was an error!", error);
      });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  width: 100%;
  height: 600px;
  background-color: #2c3e50;
}
</style>
