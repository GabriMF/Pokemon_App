<script setup>
import FileVue from "./File.vue";

const props = defineProps({
  pokemonObj: {
    type: Object,
  },
});

function showFileHero(id) {
  const visorFile = document.getElementById(id);
  visorFile.classList.remove("invisible");
}
</script>

<template>
  <li>
    <figure>
      <img :src="pokemonObj.sprites.front_default" @click="showFileHero(pokemonObj.name)">
    </figure>
    <div class="contentPokemon">
      <h3>{{ pokemonObj.name }}</h3>
      <p v-for="clase in pokemonObj.types" :class="clase.type.name">{{ clase.type.name }}</p>
    </div>
    <FileVue :id="pokemonObj.name" :pokemon="pokemonObj"></FileVue>
  </li>
</template>

<style scoped>
li {
  min-width: 190px;
  border: 1px solid #000000;
  overflow: hidden;
  transition: all 0.4s;
}


img {
  width: 100%;
  aspect-ratio: 1/1;
  object-fit: cover;
  transition: all 0.4s;
}

img:hover {
  cursor: pointer;
  transform: scale(1.8);
}

h3 {
  font-size: 16px;
  color: #2970fe;
  text-transform: uppercase;
  padding: 10px;
}

p {
  margin: 10px 30px;
  background: #999;
  text-align: center;
  border-radius: 10px;
  padding: 4px 0;
}

@media (max-width: 500px) {
  li {
    border: none;
    border-radius: 0;
    margin-bottom: 50px;
  }
}
</style>