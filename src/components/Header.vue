<script setup>
import Score from "./Score.vue";

const { score } = defineProps({
  score: Number
})

</script>

<template>
  <header class="header">
    <p class="header-left">ЗАПОМНИ СЛОВО</p>
    <div class="header-right">
      <Score :score="score" />
    </div>
  </header>
</template>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header-left {
  font-size: 16px;
  font-weight: bold;
  letter-spacing: 12%;
}

.header-right {
  display: flex;
}

</style>