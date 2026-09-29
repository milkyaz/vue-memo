<script setup>
const {label = ''} = defineProps({
  label: String,
  icon: String
})
</script>

<template>
  <button class="cs-button">{{ label }}<img v-if="icon" :src="icon" :alt="icon"></button>
</template>

<style scoped>
.cs-button {
  padding: 0;
  border: none;
  font: inherit;
  color: inherit;
  background-color: transparent;
  cursor: pointer;
}
</style>