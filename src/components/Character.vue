<template>
  <div class="character"></div>
</template>

<script>
export default {
  name: "SearchedCharacter",
  props: ["character"],
  data() {
    return {
      url: "",
    };
  },
};
</script>

<style scoped>
.character {
  width: 240px;
  height: 240px;
  margin-bottom: 20px;
  display: inline-flex;
  justify-content: center;
  align-items: flex-end;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
</style>
