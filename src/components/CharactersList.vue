<template>
  <article
    v-for="character in characters"
    :key="character.id"
    :character="character"
  >
    <h3>{{ character.name }}</h3>
  </article>
</template>

<script>
export default {
  name: "CharacterList",
  data: () => {
    return {
      characters: [],
    };
  },
  methods: {
    fetchData() {
      fetch(`https://rickandmortyapi.com/api/character`)
        .then((response) => console.log("json", response.json()))
        .then((result) => {
          console.log("result", result.data);
        });
    },
  },
};
</script>

<style scoped></style>
