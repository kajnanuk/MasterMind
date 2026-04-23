<script setup>
import { ref } from 'vue'
import Row from './Row.vue'
import Peg from './Peg.vue'

const totalAttempts = ref(10)

function createEmptyBoard() {
    const newBoard = []
    for (let i = 0; i < totalAttempts.value; i++) {
        newBoard.push({
            active: i === 0,
            pegs: new Array(4).fill(null), // 4 puste kulki
            feedback: { black: 0, white: 0 }
        })
    }
    return newBoard;
}

const board = ref(createEmptyBoard())
</script>

<template>
  <div class="board">
    <Row 
      v-for="(pojedynczyRzad, index) in board" 
      :key="index" 
      :row-data="pojedynczyRzad"
      :row-number="index + 1" 
    />
  </div>
</template>

<style scoped>
.board {
  /* To obraca widok planszy! Pierwszy element tablicy będzie na samym dole. */
  display: flex;
  flex-direction: column-reverse; 
  align-items: center; /* Wyśrodkowanie rzędów */
}
</style>