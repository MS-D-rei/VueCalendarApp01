<script setup>
  import { ref } from 'vue'
  const days = ref(['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'])
</script>

<template>
<div class="m-auto">
  <h1 class="text-2xl my-2 text-center">Vue Calendar</h1>
  <section class="flex">
    <p class="w-10 h-10 text-center" v-for="day of days" :key="day">{{ day }}</p>
  </section>
  <section class="flex">
    <p class="w-10 h-10 text-center" v-for="num in 3" :key="num">{{ num }}</p>
  </section>
</div>
</template>