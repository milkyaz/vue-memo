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

function getComponent(card) {
  if (card.state === 'closed') return ClosedCard
  return card.status === 'pending' ? OpenedCard : ResultCard
}

function handleState(id) {
  cards.value.filter(el => {
    if (el.id === id) {
      el.state = 'opened';
    }
  })
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
        @close-state="handleState"
        order="06"
        label="ПЕРЕВЕРНУТЬ"/>
  </div>
</template>

<style scoped>

</style>