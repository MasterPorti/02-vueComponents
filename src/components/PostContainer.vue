<script setup>
defineProps({
    title: String,
    description: String,

})
</script>

<template>
    <section class="p-1 bg-slate-700">
      <p class="text-lg font-bold uppercase">{{ title }}</p>
      <p>{{ description }}</p>
   </section>
</template>