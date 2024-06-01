<template>
  <h1>Rick and Morty universe</h1>

  <TheFilter
    @filter="handleFilter"
    v-model:filterName="filterName"
    v-model:filterStatus="filterStatus"
  />

  <TheList v-if="characters" :characters />
  <h2 v-else style="text-align: center">Ничего не найдено</h2>

  <ThePagination
    v-if="info"
    :info
    @changePage="changePage"
    v-model:page="page"
  />
</template>

<script setup>
import { onMounted, ref } from "vue"
import TheFilter from "./components/TheFilter.vue"
import TheList from "./components/TheList.vue"
import ThePagination from "./components/ThePagination.vue"

const characters = ref([])
const page = ref(1)
const info = ref(null)

const filterName = ref("")
const filterStatus = ref("")

function handleFilter() {
  page.value = 1
  fetchCharacters()
}

function changePage(pageNumber) {
  page.value = pageNumber
  fetchCharacters()
}

const fetchCharacters = async () => {
  const response = await fetch(
    `https://rickandmortyapi.com/api/character?page=${page.value}&name=${filterName.value}&status=${filterStatus.value}`
  )
  const data = await response.json()
  characters.value = data.results
  info.value = data.info
}

onMounted(fetchCharacters)
</script>
