<script setup>
const emit = defineEmits(['handleNext','handlePrev'])
defineProps({
    start:Number,
    end:Number,
})
</script>

<template>
     <div :class="`flex justify-between p-4 `">
   <button :class="`w-20 border-2 rounded ${end === 0? 'border-gray-500': 'border-sky-300'}`" :disabled="end === 0" @click="emit('handlePrev')">
      Previus
   </button>
   <button :class="`w-20 border-2 rounded ${start === 100? 'border-gray-500': 'border-sky-300'}`" :disabled="start === 100" @click="emit('handleNext')">
      Next
   </button>
</div>
</template>