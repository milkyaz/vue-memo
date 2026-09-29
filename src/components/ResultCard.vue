<script setup>

const {order, res} = defineProps({
  order: String,
  res: Boolean
})


function handleOrder() {
  let counterNum = Number(order) + 1;
  let numToStr = counterNum.toString();
  return numToStr.length > 1 ? numToStr : numToStr.padStart(numToStr.length + 1, '0')
}


</script>

<template>
  <div class="result-card">
    <div class="result-card__inner">
      <p class="result-card__inner-icon">
        <img v-if="res" src="./icon/res-check-icon.svg" alt="res-icon"/>
        <img v-else src="./icon/res-mark-icon.svg" alt="res-icon"/>
      </p>
      <p class="result-card__inner-order">{{ handleOrder() }}</p>
      <p class="result-card__inner-text">Автомобиль</p>
      <p class="result-card__inner-label">Завершено</p>
    </div>
  </div>
</template>

<style scoped>
.result-card {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 250px;
  height: 376px;
  box-shadow: 0px 0px 5px 0px rgba(0, 0, 0, 0.5);
  border-radius: 16px;
  cursor: pointer;
}

.result-card__inner {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px solid #CCE8FF;
  border-radius: 12px;
  width: 212px;
  height: 320px;
}

.result-card__inner-text {
  font-size: 18px;
}

.result-card__inner-icon {
  position: absolute;
  background-color: #fff;
  top: -35px;
  letter-spacing: 12%;
}

.result-card__inner-order {
  font-size: 14px;
  background-color: #fff;
  position: absolute;
  left: 17px;
  top: -23px;
}

.result-card__inner-label {
  font-size: 12px;
  line-height: 18px;
  font-weight: bold;
  background-color: #fff;
  position: absolute;
  bottom: -22px;
  letter-spacing: 12%;
}
</style>