<template>
  <div class="card_container">
    <div class="list" v-for="character in characters" :key="character.id">
      <div class="character_item">
        <div class="card_wrapper">
          <div class="character_image">
            <img v-bind:src="`${character.image}`" class="profilpicture" />
          </div>
        </div>
        <div class="details">
          <h2 class="name">{{ character.name }}</h2>
          <div class="status">
            <div
              class="status_icon"
              :class="
                `${character.status}` === 'Alive'
                  ? 'status_alive'
                  : `${character.status}` === 'Dead'
                  ? 'status_dead'
                  : 'status_unknown'
              "
            ></div>
            {{ character.status }} - {{ character.species }}
          </div>
          <div class="character_information">
            <span class="text_gray"> Last known location : </span><br />
            {{ character.location.name }} <br />
          </div>
          <div class="character_information">
            <span class="text_gray">Origin :</span> <br />
            {{ character.origin.name }}
          </div>
        </div>
      </div>
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
.card_container {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  background-color: rgb(36, 40, 47);
}
.list {
  display: flex;
  -webkit-box-pack: center;
  justify-content: center;
  -webkit-box-align: center;
  align-items: center;
  flex-wrap: wrap;
  max-width: 1920px;
}
.name {
  margin-bottom: 2px;
}
.character_item {
  width: 600px;
  height: 220px;
  display: flex;
  overflow: hidden;
  background: rgb(60, 62, 68);
  border-radius: 0.5rem;
  margin: 0.75rem;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 6px -1px,
    rgba(0, 0, 0, 0.06) 0px 2px 4px -1px;
}
.details {
  flex: 3 1 0%;
  position: relative;
  padding: 0.75rem;
  color: rgb(255, 255, 255);
  display: flex;
  flex-direction: column;
  text-align: left;
}
.card_wrapper {
  flex: 2 1 0%;
  width: 100%;
}
.character_image {
  width: 100%;
  height: 100%;
  margin: 0px;
  opacity: 1;
  transition: opacity 0.5s ease 0s;
  object-position: center center;
  object-fit: cover;
}
.status {
  display: flex;
  align-items: center;
  font-size: 14px;
  text-transform: capitalize;
}

.status_alive {
  height: 0.5rem;
  width: 0.5rem;
  margin-right: 0.375rem;
  background: rgb(85, 204, 68);
  border-radius: 50%;
}
.status_dead {
  height: 0.5rem;
  width: 0.5rem;
  margin-right: 0.375rem;
  background: rgb(214, 61, 46);
  border-radius: 50%;
}
.status_unknown {
  height: 0.5rem;
  width: 0.5rem;
  margin-right: 0.375rem;
  background: rgb(158, 158, 158);
  border-radius: 50%;
}
.character_information {
  margin-top: 18px;
  margin-bottom: 5px;
}

.text_gray {
  color: rgb(158, 158, 158);
}
</style>
