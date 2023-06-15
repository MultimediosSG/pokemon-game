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
  pokemonArr.value = await getPokemonOptions()

  const rndInt = Math.floor(Math.random() * 4)
  pokemon.value = pokemonArr.value[rndInt]
}
function checkAnswer(selectedId) {
  showPokemon.value = true
  showAnswer.value = true

  if (selectedId === pokemon.value.id) {
    message.value = `Correcto, ${pokemon.value.name}`
  } else {
    message.value = `Oops, era ${pokemon.value.name}`
  }
}
function newGame() {
  showPokemon.value = false
  showAnswer.value = false
  pokemonArr.value = []
  pokemon.value = null
  mixPokemonArray()
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

