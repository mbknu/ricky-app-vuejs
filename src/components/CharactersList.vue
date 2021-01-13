<template>
  <div class="list" v-for="character in characters" :key="character.id">
    <div class="details">
      <img v-bind:src="`${character.image}`" class="profilpicture" />
      {{ character.name }}
      {{ character.status }}
      {{ character.species }} <br />

      Last know location : {{ character.location.name }} First seen in :
      {{ character.origin.name }}
    </div>
  </div>
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
      function getRandom() {
        const randomNumber = Math.floor(Math.random() * 672);
        const randomNumber1 = Math.floor(Math.random() * 672);
        const randomNumber2 = Math.floor(Math.random() * 672);
        const randomNumber3 = Math.floor(Math.random() * 672);
        const randomNumber4 = Math.floor(Math.random() * 672);
        const randomNumber5 = Math.floor(Math.random() * 672);

        const total = `${randomNumber}, ${randomNumber1}, ${randomNumber2}, ${randomNumber3}, ${randomNumber4}, ${randomNumber5}`;
        return total;
      }

      fetch(`https://rickandmortyapi.com/api/character/[${getRandom()}]`)
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
}
</style>
