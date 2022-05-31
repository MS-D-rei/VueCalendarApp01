<script setup>
  import { ref, computed } from 'vue'
  const days = ref(['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'])
  const months = ref(["January","February","March","April","May","June","July","August","September","October","November","December"])
  const today = new Date()
  const currentMonth = months.value[today.getMonth()] // getMonth returns 0 to 11
  const currentYear = today.getFullYear()

  function daysInMonth() {
    const daysOfTheMonth = new Date(today.getFullYear(), today.getMonth() + 1, 0).getDate()
    return daysOfTheMonth
  }
</script>

<template>
<div class="m-auto">
  <h1 class="text-2xl my-2 text-center">Vue Calendar</h1>
  <section class="mx-5 flex justify-between">
    <h2 class="font-bold">{{ currentMonth }}</h2>
    <h2 class="font-bold">{{ currentYear }}</h2>
  </section>
  <section class="flex my-2">
    <p
      class="text-center"
      style="width: 14.28%"
      v-for="day of days"
      :key="day"
    >
      {{ day }}
    </p>
  </section>
  <section class="flex flex-wrap">
    <p
      class="text-center"
      style="width: 14.28%"
      v-for="num in daysInMonth()"
      :key="num"
    >
      {{ num }}
    </p>
  </section>
</div>
</template>