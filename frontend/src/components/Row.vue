<script setup>
import Peg from './Peg.vue'
// Odbieramy nasz nowy argument
const props = defineProps({
  rowData: Object,
  rowNumber: Number = null
})

const emit = defineEmits(['kliknieto-kulke'])
</script>

<template>
  <div class="row">
    
    <strong>{{ props.rowNumber }}.</strong> 
    [
    <span v-if="props.rowData.active"
      v-for="(peg, idx) in props.rowData.pegs" 
      :key="idx" 
      style="cursor: pointer; text-decoration: underline; margin: 0 5px;"
      id="aktywny"
      @click="emit('kliknieto-kulke', idx)" 
    >
      {{ peg === null ? 'puste' : peg }}
    </span>
    <span v-else>
      {{ props.rowData.pegs.map(peg => peg === null ? 'puste' : peg).join(', ') }}
    </span>
    ]
    

    
    
    białe: {{ props.rowData.feedback.white }} 
    czarne: {{ props.rowData.feedback.black }}

    

  </div>
</template>

<style scoped>
   #aktywny {
  font-weight: bold;
  color: green;
    }
</style>

