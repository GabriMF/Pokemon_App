<script setup>
import { RouterView } from 'vue-router'
import HeaderGlobal from './components/HeaderGlobal.vue'
import FooterGlobal from './components/FooterGlobal.vue'
</script>

<template>
  <HeaderGlobal textHOne="POKEMONS!" />
  <RouterView />
  <FooterGlobal />
</template>