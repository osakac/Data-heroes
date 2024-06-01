<template>
  <div class="filter">
    <input
      class="filter__input"
      type="search"
      v-model="filterName"
      placeholder="Поиск по имени"
    />
    <input
      class="filter__input"
      type="search"
      v-model="filterStatus"
      placeholder="Поиск по статусу"
    />
    <button @click="$emit('filter')">Применить</button>
  </div>
</template>

<script setup>
const filterName = defineModel("filterName")
const filterStatus = defineModel("filterStatus")
</script>
