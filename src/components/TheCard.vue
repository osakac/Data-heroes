<template>
  <li class="card">
    <img :src="props.character.image" :alt="props.character.name" />

    <div class="card__info">
      <h3>{{ props.character.name }}</h3>
      <p>
        {{ props.character.status }} -
        {{ props.character.species }}
      </p>
      <p>
        <span>Last known location:</span><br />
        {{ props.character.location.name }}
      </p>
      <p>
        <span>First seen:</span><br />
        {{ props.character.origin.name }}
      </p>
    </div>
  </li>
</template>

<script setup lang="ts">
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
  character: Object as () => Character,
})
</script>
