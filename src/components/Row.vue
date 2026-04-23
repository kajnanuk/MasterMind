<script setup>
// Odbieramy nasz nowy argument
const props = defineProps({
  rowData: Object,
  rowNumber: Number = null
})
</script>

<template>
  <div style="font-family: monospace; font-size: 18px; margin: 10px 0;">
    
    <strong>{{ props.rowNumber }}.</strong> 
    
    [ {{ props.rowData.pegs.map(peg => peg === null ? 'puste' : peg).join(', ') }} ] 
    
    białe: {{ props.rowData.feedback.white }} 
    czarne: {{ props.rowData.feedback.black }}
    
    <span v-if="props.rowData.active" style="color: green; margin-left: 5px;">
      <-AKTYWNY RZĄD
    </span>

  </div>
</template>