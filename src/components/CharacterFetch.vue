<script setup>
import { onMounted } from "vue"
import { ref } from "vue"

const props = defineProps(['characterId'])

const character = ref([]);
const charOrigin = ref([])
onMounted (async () => {
    character.value = await fetch('https://rickandmortyapi.com/api/character/' + props.characterId)
        .then(response => response.json())
        .then(response => response)

    console.log('character',character.value)
    charOrigin.value = character.value.origin
})
</script>

<template>
    <main>
        <ul>
            <img :src="character.image">
            <li>Name: {{ character.name }}</li>
            <li>Status: {{ character.status }}</li>
            <li>Species: {{ character.species }}</li>
            <li>Gender: {{ character.gender }}</li>
            <li>Origin: {{ charOrigin.name }}</li>
        </ul>
    </main>
</template>