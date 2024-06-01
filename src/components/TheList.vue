<template>
  <ul class="list">
    <TheCard
      v-for="character in props.characters"
      :key="character.id"
      :character="character"
    />
  </ul>
</template>

<script setup lang="ts">
import TheCard from "./TheCard.vue"

interface Character {
  id: number
  name: string
  image: string
  status: string
  species: string
  location: {
    name: string
  }
  origin: {
    name: string
  }
}

const props = defineProps({
  characters: Array<Character>,
})
</script>
