<script setup>

import OpenedCard from "./OpenedCard.vue";
import ClosedCard from "./ClosedCard.vue";
import {ref} from "vue";
import ResultCard from "./ResultCard.vue";

const cards = ref([
  {word: 'car', translation: 'машина', state: 'closed', status: 'pending', id: crypto.randomUUID()},
  {word: 'apple', translation: 'яблоко', state: 'opened', status: 'pending', id: crypto.randomUUID()},
  {word: 'fear', translation: 'страх', state: 'opened', status: 'res', id: crypto.randomUUID()},
])

const variantOption = ref('');

function getComponent(card) {
  if (card.state === 'closed') return ClosedCard
  return card.status === 'pending' ? OpenedCard : ResultCard
}

function handleState(id) {
  const card = cards.value.find(el => el.id === id)
  if (card) card.state = 'opened'
}

function handleStatus(id, variant) {
  const card = cards.value.find(el => el.id === id)
  variantOption.value = variant;
  if (card) card.status = 'res'
}
</script>

<template>
  <div v-for="card in cards" :key="card.id">
    <component
        :is="getComponent(card)"
        :close-text="card.word"
        :open-text="card.translation"
        :result-text="card.translation"
        :state="card.state"
        :id="card.id"
        :variant="variantOption"
        @close-state="handleState"
        @submit-selection="handleStatus"
        order="06"
        label="ПЕРЕВЕРНУТЬ"/>
  </div>
</template>

<style scoped>

</style>