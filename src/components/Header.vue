<script setup>
import Score from "./Score.vue";
</script>

<template>
  <header class="header">
    <p class="header-left">ЗАПОМНИ СЛОВО</p>
    <div class="header-right">
      <Score />
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