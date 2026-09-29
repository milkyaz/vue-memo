<script setup>

import OpenedCard from "./OpenedCard.vue";
import ClosedCard from "./ClosedCard.vue";
import {ref} from "vue";
import ResultCard from "./ResultCard.vue";

const isSelector = ref(true);
const orderCard = ref('');
const memoTextCard = ref('');
const result = ref(false);
const isResultCard = ref(false);
const orderCardResult = ref('')

function handleClick(order, memoText) {
  orderCard.value += order;
  memoTextCard.value = memoText;
  isSelector.value = false;
}

function handleResult(res, order, isResultCardVal) {
  result.value = res;
  orderCardResult.value = order;
  isResultCard.value = isResultCardVal;
}
</script>

<template>
  <ClosedCard v-if="isSelector" @opened="handleClick" order="06" memo-text="car" label="ПЕРЕВЕРНУТЬ"/>
  <OpenedCard v-else-if="!isResultCard" :order="orderCard" :memo-text="memoTextCard" @result="handleResult"/>
  <ResultCard v-else :order="orderCardResult" :res="result"/>
</template>

<style scoped>

</style>