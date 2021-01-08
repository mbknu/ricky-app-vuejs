<template>
  <input
    placeholder="Search characters..."
    v-model="searchValue"
    @input="onInput"
  />
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      searchValue: "",
      timeout: null,
    };
  },
  methods: {
    onInput() {
      clearTimeout(this.timeout);
      this.timeout = setTimeout(() => {
        this.search();
      }, 800);
    },
    search() {
      fetch(
        `https://rickandmortyapi.com/api/character/?name=${this.searchValue}`
      )
        .then((response) => response.json())
        .then((result) => {
          this.$emit("fetch-characters", result.data);
        });
    },
  },
};
</script>

<style scoped>
input {
  padding: 10px 16px;
  border-radius: 4px;
  font-size: 18px;
  outline: 0;
  border: 2px solid #5f5f5f;
  display: block;
}

input:focus {
  border-color: rgb(255, 152, 0);
}
</style>
