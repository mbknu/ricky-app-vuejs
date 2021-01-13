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
      function getSixRandomCharacter(length) {
        let randomArray = [];
        do {
          let random = Math.floor(Math.random() * 672);
          randomArray =
            randomArray.indexOf(random) > -1
              ? randomArray
              : randomArray.concat(random);
        } while (randomArray.length < length);

        return randomArray;
      }

      const res = getSixRandomCharacter(6);

      fetch(`https://rickandmortyapi.com/api/character/${res}`)
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
