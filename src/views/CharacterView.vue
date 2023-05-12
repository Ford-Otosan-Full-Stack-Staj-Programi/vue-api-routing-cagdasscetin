<script setup>
import CharacterFetch from '@/components/CharacterFetch.vue';


</script>

<template>
    <CharacterFetch :characterId="$route.params.id"></CharacterFetch>
</template>