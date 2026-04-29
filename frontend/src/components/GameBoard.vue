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



function checkRow(rowIndex = board.value.findIndex(row => row.active)) {
    const row = board.value[rowIndex]

    //przykladowe
    row.feedback.black = Math.floor(Math.random() * 5) 
    row.feedback.white = Math.floor(Math.random() * (5 - row.feedback.black)) 

    row.active = false
    if (rowIndex + 1 < board.value.length) {
        board.value[rowIndex + 1].active = true
    }

    else {
        alert("Koniec gry! Nie masz więcej prób.")
    }
}


function cleanRow(rowIndex) {
    const row = board.value[rowIndex]
    row.pegs = new Array(4).fill(null)
}


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

  <div class= "pegs">
    <Peg color="red" />
    <Peg color="blue" />
    <Peg color="green" />
    <Peg color="yellow" />
    <Peg color="purple" />
    <Peg color="orange" />
    <button class="check-button" @click="checkRow">
        Sprawdź
    </button>
        <button class="clean-button" @click="cleanRow">
        Wyczyść
    </button>
  </div>  
 



</template>

<style scoped>
.board {
  /* To obraca widok planszy! Pierwszy element tablicy będzie na samym dole. */
  display: flex;
  flex-direction: column-reverse; 
  align-items: center; /* Wyśrodkowanie rzędów */
}

.pegs {
  display: flex;
  background-color: #6e4242;
  padding: 10px;
  border-radius: 8px;
  justify-content: center;
  margin-top: 20px;
  cursor: pointer;
}

.check-button{
  font-size: 16px;
  left: 10px;
  padding: 10px;
  background-color: #4a9eb7;
  border-radius: 12px;
  cursor: pointer;
}

.clean-button{
    font-size: 16px;
  left: 10px;
  padding: 10px;
  background-color: #d35ea8;
  border-radius: 12px;
  cursor: pointer;
}




</style>