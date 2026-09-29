<script setup>
import {ref} from "vue";

const { order, memoText } = defineProps({
  order: String,
  memoText: String,
  label: String
})
const isMark = ref(false);
const isCheck = ref(true);
const otherMemoText = "Яблоко";
const res = otherMemoText === memoText;
const emit = defineEmits(['result'])
const isResultCard = ref(false);

function handleOrder() {
  let counterNum = Number(order) + 1;
  let numToStr = counterNum.toString();
  return numToStr.length > 1 ? numToStr : numToStr.padStart(numToStr.length + 1, '0')
}

function handleMark() {
  return emit('result',isMark.value === res, handleOrder(), isResultCard.value = true);
}

function handleCheck() {
  return emit('result', isCheck.value === res, handleOrder(), isResultCard.value = true);
}

</script>

<template>
  <div class="opened-card">
    <div class="opened-card__inner">
      <p class="opened-card__inner-order">{{ handleOrder() }}</p>
      <p class="opened-card__inner-text">{{ otherMemoText }}</p>
      <p class="opened-card__inner-label">
        <img style="  cursor: pointer;" src="./icon/mark-opened-icon.svg" alt="check" width="24" @click="handleMark">
        <img style="  cursor: pointer;" src="./icon/check-opened-icon.svg" alt="check" width="24" @click="handleCheck">
      </p>
    </div>
  </div>
</template>

<style scoped>
.opened-card {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 250px;
  height: 376px;
  box-shadow: 0px 0px 5px 0px rgba(0, 0, 0, 0.5);
  border-radius: 16px;
}

.opened-card__inner {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px solid #CCE8FF;
  border-radius: 12px;
  width: 212px;
  height: 320px;
}

.opened-card__inner-text {
  font-size: 18px;
}

.opened-card__inner-order {
  font-size: 14px;
  background-color: #fff;
  position: absolute;
  left: 17px;
  top: -23px;
}

.opened-card__inner-label {
  display: flex;
  gap: 32px;
  padding: 0 8px;
  font-size: 12px;
  line-height: 18px;
  font-weight: bold;
  background-color: #fff;
  position: absolute;
  bottom: -22px;
  letter-spacing: 12%;
}
</style>