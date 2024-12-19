<template>
  <div v-if="event">
    <h2>{{ event.title }}</h2>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<script setup>
import EventService from '@/services/EventService'
import { ref, onMounted } from 'vue'
const event = ref(null)
onMounted(() => {
  EventService.getEvent(123)
    .then((response) => (event.value = response.data))
    .catch((error) => console.log(error))
})
</script>
