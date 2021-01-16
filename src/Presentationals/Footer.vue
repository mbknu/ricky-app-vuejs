<template>
  <div class="wrapper">
    <a href="https://github.com/mbknu" target="_blank" rel="noopener"
      ><img src="../assets/github.png" alt="github-logo" width="30"
    /></a>
    <div v-for="information in informations" :key="information.id">
      test
    </div>
  </div>
</template>

<script>
export default {
  name: "Footer",
  data: () => {
    return {
      informations: [],
    };
  },
  mounted() {
    this.fetchData();
  },
  methods: {
    fetchData() {
      fetch(`https://rickandmortyapi.com/api/character/`)
        .then((response) => response.json())
        .then((data) => {
          this.informations = data;
        });
      console.log("info", this.informations);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.wrapper {
  width: 100%;
  height: 250px;
  background-color: rgb(32, 35, 41);
}
.test {
  color: white;
}
</style>
