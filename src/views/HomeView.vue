<script setup>
import PokemonOptions from "@/components/PokemonOptions.vue";
import PokemonPicture from "@/components/PokemonPicture.vue";
import usePokemonOptions from "@/composables/usePokemonOptions";

import { onMounted, ref } from "vue";
const { getPokemonOptions } = usePokemonOptions();

const pokemonArr = ref([]);
const pokemon = ref(null);
const showPokemon = ref(false);
const showAnswer = ref(false);
const message = ref("");


async function mixPokemonArray() {
  
}
function checkAnswer(selectedId) {
 
}
function newGame() {
 
}

onMounted(() => {
  mixPokemonArray()
})

</script>

<template>
  <h1 v-if="!pokemon">Espere por favor...</h1>

  <div v-else>
    <h1>¿Quién es este pokémon?</h1>

    <PokemonPicture :pokemon-id="pokemon.id" :show-pokemon="showPokemon" />

    <PokemonOptions :pokemons="pokemonArr" @selection-pokemon="checkAnswer" />

    <template v-if="showAnswer">
      <h2 class="fade-in">{{ message }}</h2>
      <button @click="newGame">Nuevo Juego</button>
    </template>
  </div>
</template>

