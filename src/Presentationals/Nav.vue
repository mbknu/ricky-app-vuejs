<template>
  <div class="container">
    <div class="links">
      <ul>
        <li>Search</li>
        <li>
          <a href="https://rickandmortyapi.com/" target="_blank" rel="noopener"
            >Doc</a
          >
        </li>
        <li>About</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Nav",
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  font-size: 20px;
  margin-top: 0;
  margin-bottom: 0;
  margin-right: 0;
  margin-bottom: 70px;
  width: 100%;
}
.links {
  width: 30%;
  margin-left: 70%;
}
li {
  display: inline-block;
  cursor: pointer;
  font-weight: bold;
}
li:hover {
  color: rgb(255, 152, 0);
  transition: all 0.1s ease 0s;
}
ul {
  display: flex;
  justify-content: space-around;
}
a {
  text-decoration: none;
  color: #2c3e50;
}

a:hover {
  color: rgb(255, 152, 0);
  transition: all 0.1s ease 0s;
}
</style>
