<template>
  <h3>{{ characters.results }}</h3>
</template>

<script>
export default {
  name: "CharacterList",
  data: () => {
    return {
      characters: [],
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
          this.characters = data;
        });
    },
  },
};
</script>

<style scoped></style>
