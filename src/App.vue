<script setup>
import { ref } from 'vue'


const count = ref(0)
function increment(num) {
  count.value+=num
}

const decrement = () => {
  count.value--
}

decrement()

</script>



<template>
  
  <h1>Mój pierwszy licznik Vue!</h1>
  <button @click="decrement()" id='button123'>
    Licznik to: {{ count }}
  </button>

</template>

<style scoped>
#button123 {
  font-weight: bold;
  background-color: #42b983;
}
 </style>