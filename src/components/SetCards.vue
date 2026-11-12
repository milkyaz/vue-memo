<script setup>

import OpenedCard from "./OpenedCard.vue";
import ClosedCard from "./ClosedCard.vue";
import {ref} from "vue";
import ResultCard from "./ResultCard.vue";

const cards = ref([
  {word: 'car', translation: 'машина', state: 'closed', status: 'pending', id: crypto.randomUUID(), variant: ''},
  {word: 'apple', translation: 'яблоко', state: 'closed', status: 'pending', id: crypto.randomUUID(), variant: ''},
  {word: 'fear', translation: 'страх', state: 'closed', status: 'pending', id: crypto.randomUUID(), variant: ''},
])

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

  if (card) {
    card.status = 'res';
    card.variant = variant;
  }
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
        :variant="card.variant"
        @close-state="handleState"
        @submit-selection="handleStatus"
        order="06"
        label="ПЕРЕВЕРНУТЬ"/>
  </div>
</template>

<style scoped>

</style>