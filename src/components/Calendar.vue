<script setup>
  import { ref, computed } from 'vue'
  const days = ref(['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'])
  const months = ref(["January","February","March","April","May","June","July","August","September","October","November","December"])
  const today = new Date()
  const currentMonth = ref(today.getMonth()) // getMonth returns 0 to 11
  const currentMonthName = computed( () => {
    return months.value[currentMonth.value]
  })
  const currentYear = ref(today.getFullYear())
  const currentDate = ref(today.getDate())

  function daysInMonth() {
    return new Date(currentYear.value, currentMonth.value + 1, 0).getDate() // return the last date number
  }

  function startDayIndex() {
    return new Date(currentYear.value, currentMonth.value, 1).getDay()
  }

  function nextMonth() {
    if (currentMonth.value == 11) {
      currentMonth.value = 0
      currentYear.value++
    } else {
      currentMonth.value++
    }
  }

  function previousMonth() {
    if (currentMonth.value == 0) {
      currentMonth.value = 11
      currentYear.value--
    } else {
      currentMonth.value--
    }
  }
</script>

<template>
<div class="m-auto">
  <h1 class="text-2xl my-2 text-center">Vue Calendar</h1>
  <section class="mx- flex justify-between">
    <h2 class="font-bold">{{ currentMonthName }}</h2>
    <h2 class="font-bold">{{ currentYear }}</h2>
    <h2 class="font-bold">{{ currentDate }}</h2>
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
      v-for="num in startDayIndex()"
      :key="num"
      :class="currentDateHighlight(num)"
    >
    </p>
    <p
      class="text-center"
      style="width: 14.28%"
      v-for="num in daysInMonth()"
      :key="num"
    >
      {{ num }}
    </p>
  </section>
  <section class="flex justify-between my-4 mx-5">
    <button class="px-2 border rounded" @click="previousMonth">Prev</button>
    <button class="px-2 border rounded" @click="nextMonth">Next</button>
  </section>
</div>
</template>