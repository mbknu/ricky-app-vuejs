<template>
  <div class="list" v-for="character in characters" :key="character.id">
    <div class="details">
      <img v-bind:src="`${character.image}`" class="profilpicture" />
      <h3>{{ character.name }}</h3>
      {{ character.status }}
      {{ character.species }} <br />

      Last known location : {{ character.location.name }} <br />
      Origin : {{ character.origin.name }}
    </div>
  </div>
</template>

<script>
import uniq from "lodash.uniq";
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
      function getRandomCharacters(length) {
        const randomArray = new Array(length).fill().map(() => {
          return Math.floor(Math.random() * 672);
        });

        return uniq(randomArray);
      }

      const getRandomCharacter = getRandomCharacters(6);

      fetch(`https://rickandmortyapi.com/api/character/${getRandomCharacter}`)
        .then((response) => response.json())
        .then((data) => {
          this.characters = data;
          console.log("data", data);
        });
    },
  },
};
</script>

<style scoped>
.list {
  display: flex;
  justify-content: space-evenly;
  margin-bottom: 50px;
  width: 100%;
}
.details {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 250px;
}
</style>
