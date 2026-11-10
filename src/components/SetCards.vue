<script setup>

import OpenedCard from "./OpenedCard.vue";
import ClosedCard from "./ClosedCard.vue";
import {ref} from "vue";
import ResultCard from "./ResultCard.vue";

const cards = ref([
  { word: 'car', translation: 'машина', state: 'closed', status: 'pending' },
  { word: 'apple', translation: 'яблоко', state: 'opened', status: 'pending' },
  { word: 'apple', translation: 'яблоко', state: 'opened', status: 'res' },
])

function getComponent(card) {
  if (card.state === 'closed') return ClosedCard
  return card.status === 'pending' ? OpenedCard : ResultCard
}
</script>

<template>
  <div  v-for="(card, i) in cards" :key="i">
    <component :is="getComponent(card)" order="06" :memo-text="card.word" label="ПЕРЕВЕРНУТЬ" />
  </div>
</template>

<style scoped>

</style>