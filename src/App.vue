<script setup>
import Header from "./components/Header.vue";
import SetCards from "./components/SetCards.vue";
import { ref } from "vue";

const score = ref(100);

</script>

<template>
  <div class="wrapp">
    <Header :score="score" />
    <SetCards/>
  </div>
</template>
<style scoped>
.wrapp {
  padding: 37px 62px 0 66px;
}
</style>
