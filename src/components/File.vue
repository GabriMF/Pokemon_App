<script setup>
const props = defineProps({
  pokemon: {
    type: Object,
    default: null,
  },
  id: {
    type: String,
    default: null,
  },
});

function goInvisible(id) {
  const visor = document.getElementById(id);
  visor.classList.add("invisible");
}
</script>

<template>
  <div :id="id" class="invisible visor">
    <div class="fileDetails">
      <button @click="goInvisible(id)">X</button>
      <img :src="pokemon.sprites.front_default" :alt="pokemon.name" />
      <div class="pokemonInformation">
        <h4>{{ pokemon.name }}</h4>
        <h5 class="specie">Specie:</h5>
        <p>{{ pokemon.species.name }}</p>
        <h5 class="types">Type:</h5>
        <p v-for="clase in pokemon.types" :class="clase.type.name">{{ clase.type.name }}</p>
        <h5 class="stats">Stat:</h5>
        <p v-for="stat in pokemon.stats">{{ stat.stat.name }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.visor {
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.5);
  padding: 10vw;
  position: absolute;
  top: 0px;
  left: 0px;
  z-index: 10001;
  position: fixed;
}

.fileDetails {
  width: 100%;
  height: 100%;
  background: #fff;
  border-radius: 20px;
  padding: 30px 90px 30px 30px;
  position: relative;
  display: flex;
}

button {
  position: absolute;
  top: 30px;
  right: 30px;
  display: inline-block;
  background-color: #ff9801;
  padding: 10px;
  border-radius: 10px;
  color: #fff;
  font-weight: bold;
  border: 3px solid #ff9801;
}

button:hover {
  border: 3px solid #ff9801;
  background-color: #fff;
  color: #ff9801;
}

.fileDetails p {
  color: #000;
  margin: 5px;
}

.invisible {
  display: none;
}

.pokemonInformation {
  margin: 0 0 30px 30px;
  overflow: auto;
  width: 100%;
}

h4 {
  font-size: 24px;
  color: #2970fe;
  text-transform: capitalize;
  margin-bottom: 25px;
}

h5 {
  margin-top: 10px;
  font-size: 20px;
  font-weight: normal;
  font-style: oblique;
  text-transform: capitalize;
}

h5 ~ p {
  width: 200px;
  margin: 10px 30px;
  background: #ccc;
  text-align: center;
  border-radius: 10px;
  padding: 4px 0;
}

h5.types ~ p.grass {
  background: #9bcc50;
}

h5.types ~ p.poison {
  background: #b97fc9;
}

h5.types ~ p.fire {
  background: #fd7d24;
}

h5.types ~ p.water {
  background: #4592c4;
}

h5.types ~ p.flying {
  background: linear-gradient(180deg, #3dc7ef 50%, #bdb9b8 50%);
}

h5.types ~ p.bug {
  background: #729f3f;
}
/* Normal: #a4acaf
Eléctrico: #eed535
Hada: fdb9e9
Lucha: #d56723
Psíquico: #f366b9
Roca: #a38c21
Hielo: #51c4e7
Fantasma: #7b62a3
Acero: #9eb7b8
Siniestro: #707070

Tierra: linear-gradient(180deg, #f7de3f 50%, #ab9842 50%)
Dragón: linear-gradient(180deg, #53a4cf 50%, #f16e57 50%) */

@media (max-width: 1264px) {
  .fileDetails {
    flex-direction: column;
    overflow: auto;
    margin: 0 60px 0 0;
  }

  .pokemonInformation {
    margin: 0 0 0 0;
    overflow: initial;
    width: auto;
  }

  .fileDetails img {
    width: 100%;
    aspect-ratio: 1/0.5;
    object-fit: cover;
  }

  h4 {
    margin-top: 20px;
  }
}
</style>
