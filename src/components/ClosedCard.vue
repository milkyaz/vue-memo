<script setup>
const { order, memoText, label } = defineProps({
  order: String,
  memoText: String,
  label: String
})

const emit = defineEmits(['opened']);

function clickCard() {
  emit('opened', order, memoText)
}
</script>

<template>
<div class="closed-card" @click="clickCard">
  <div class="closed-card__inner">
    <p class="closed-card__inner-order">{{ order }}</p>
    <p class="closed-card__inner-text">{{ memoText }}</p>
    <p class="closed-card__inner-label">{{ label }}</p>
  </div>
</div>
</template>

<style scoped>
.closed-card {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 250px;
  height: 376px;
  box-shadow: 0px 0px 5px 0px rgba(0, 0, 0, 0.5);
  border-radius: 16px;
  cursor: pointer;
}
.closed-card__inner {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px solid #CCE8FF;
  border-radius: 12px;
  width: 212px;
  height: 320px;
}
.closed-card__inner-text {
  font-size: 18px;
}
.closed-card__inner-order {
  font-size: 14px;
  background-color: #fff;
  position: absolute;
  left: 17px;
  top: -23px;
}
.closed-card__inner-label {
  font-size: 12px;
  line-height: 18px;
  font-weight: bold;
  background-color: #fff;
  position: absolute;
  bottom: -22px;
  letter-spacing: 12%;
}
</style>