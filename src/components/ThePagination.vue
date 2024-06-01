<template>
  <div>
    <span>Страница: </span>
    <select @change="changePage($event.target.value)" v-model="page">
      <option v-for="page in props.info.pages" :value="page">
        {{ page }}
      </option>
    </select>
  </div>
</template>

<script setup>
const props = defineProps({
  info: Object,
})

const emit = defineEmits(["changePage"])

const page = defineModel("page")

const changePage = (page) => emit("changePage", page)
</script>
