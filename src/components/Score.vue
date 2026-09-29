<script setup>
import HeaderIcon from "./icon/header-icon.svg"

const {score = 100} = defineProps({
  score: Number
})
</script>

<template>
  <div class="score">
    <p>{{ score }}</p>
    <img :src="HeaderIcon" alt="icon">
  </div>

</template>

<style scoped>
.score {
  width: 114px;
  display: flex;
  justify-content: center;
  gap: 10px;
  align-items: center;
  background-color: var(--bg-primary);
  border-radius: 36px;
  color: var(--button-primary);
  font-weight: bold;
  font-size: 16px;
}
</style>