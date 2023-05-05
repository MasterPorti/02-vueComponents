<script setup>
import { ref } from 'vue';
import ButtonsCarousel from './components/ButtonsCarousel.vue'
import PostContainer from './components/PostContainer.vue'

const data = ref([])

fetch('https://jsonplaceholder.typicode.com/posts')
.then((res) => res.json())
.then((res) => data.value = res)
.finally(() => console.log('termino'))

const start = ref(10)

const end = ref(0)


const handleNext = () => {
   if(start.value != 100) {
      start.value = start.value + 10
      end.value = end.value + 10
   }

}

const handlePrev = () => {
   if(end.value != 0) {
      end.value = end.value - 10
      start.value = start.value + 10

   }

}

</script>

<template>
   <main v-if="data.length === 0">CARGANDO ......</main>
   <main v-if="data.length > 0" class="w-[40%] mx-auto" >
      <ButtonsCarousel @handleNext="handleNext" @handlePrev="handlePrev" :start="start" :end="end"/>
   <div class="flex flex-col gap-2">
      <PostContainer v-for="post in data.slice(end,start)" :title="post.title" :description="post.body" :key="post.id" />
   </div>
   </main>
</template>


