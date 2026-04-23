<script setup>
import { ref } from 'vue'
import GameBoard from './components/GameBoard.vue'
import Row from './components/Row.vue';

</script>


<template>
  <div class="app-container">
    
    <GameBoard />
    
  </div>
</template>

<style scoped>

/* Trochę podstawowego wyglądu, żeby gra była na środku ekranu */
.app-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: sans-serif;
  margin-top: 50px;
}
</style>