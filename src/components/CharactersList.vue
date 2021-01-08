<template>
  <character
    v-for="character in characters"
    :key="character.id"
    :character="character"
  />
</template>

<script>
import Character from "./Character";
export default {
  name: "CharacterList",
  components: { Character },
  props: {
    characters: Array,
  },
};
</script>
