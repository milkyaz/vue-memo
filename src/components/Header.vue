<script setup>
import HeaderIcon from "./icon/header-icon.svg"
import BaseButton from "./BaseButton.vue";
</script>

<template>
  <header class="header">
    <p class="header-left">ЗАПОМНИ СЛОВО</p>
    <div class="header-right">
      <BaseButton class="header-right__btn" :icon="HeaderIcon" label="100"/>
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

.header-right__btn {
  width: 114px;
  display: flex;
  gap: 10px;
  align-items: center;
  background-color: var(--bg-primary);
  padding: 12px 24px 12px;
  border-radius: 36px;
  color: var(--button-primary);
  font-weight: bold;
  font-size: 16px;
}

.header-right__btn:active {
  background-color: var(--bg-primary-hover);
}
</style>