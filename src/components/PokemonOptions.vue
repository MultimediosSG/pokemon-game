<script setup>
defineProps({
    pokemons: {
        type: Array,
        required: true
    }
});

</script>
<template>
    <div class="options-container">
        <ul>
            <li>
               opcion 1
            </li>
            <li>
               opcion 2
            </li>
            <li>
               opcion 3
            </li>
            <li>
               opcion 4
            </li>
        </ul>

    </div>
</template>
  

  
<style scoped>
ul {
    list-style-type: none;
}

li {
    background-color: white;
    border-radius: 5px;
    border: 1px solid rgba(0, 0, 0, 0.2);
    cursor: pointer;
    margin-bottom: 10px;
    width: 250px;
}

li:hover {
    background-color: rgba(0, 0, 0, 0.05);
}

.options-container {
    display: flex;
    justify-content: center;
}
</style>
  