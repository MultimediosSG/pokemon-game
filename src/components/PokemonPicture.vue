<script setup>
import { computed } from 'vue';

const props = defineProps({
    pokemonId: {
        type: Number,
        required: true
    },
    showPokemon: {
        type: Boolean,
        required: true,
        default: false
    }
})
const imgSrc = computed(() => {

    return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${props.pokemonId}.svg`

});
</script>
<template>
    <div class="pokemon-container">

        <img v-if="!showPokemon" :src="imgSrc" class="hidden-pokemon" alt="pokemon">

        <img v-else :src="imgSrc" class="fade-in" alt="pokemon">

    </div>
</template>
  

  
<style scoped>
.pokemon-container {
    height: 200px;
}
img {
    height: 200px;
    user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    -webkit-user-drag: none;
    -webkit-user-select: none;
}
.hidden-pokemon {
    filter: brightness(0);
}
</style>
  