<script setup>
import { onMounted } from "vue"
import { ref } from "vue"

const datas = ref({});


onMounted (async () => {
    datas.value = await fetch('https://rickandmortyapi.com/api/character')
        .then(response => response.json())
        .then(response => response.results)

    console.log('datas',datas)
})
</script>

<template>
    <main>
        <div class="images">
            <template v-for="character in datas" :key="character.id"> 
                <div class="images__item">
                    <nav>
                        <RouterLink :to="'/character/' + character.id">
                            <img :src="character.image" >{{ character.name }}
                        </RouterLink>
                    </nav>
                </div>
            </template>
        </div>
    </main>
</template>

<style lang="scss" scoped>
.images {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-items: flex-start;
  justify-content: flex-start;


  &__item {
    width: calc(90% / 4);
    aspect-ratio: 4/3;

    padding: 10px;

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }

}
</style>