<script setup>
import { ref } from 'vue'

const props = defineProps({
  color: String
})


</script>


<template>
  <div class="peg" :style="{ backgroundColor: props.color }">
    
  </div>
</template>
<style scoped>
  .peg {
    width: 30px;
    height: 30px;
    border-radius: 50%;
    margin: 0 5px;
  }

  
</style>
