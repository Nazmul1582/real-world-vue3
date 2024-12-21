<template>
  <div v-if="event">
    <h2>{{ event.title }}</h2>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
    <p>Event #{{ route.params.id }}</p>
  </div>
</template>

<script setup>
import EventService from '@/services/EventService'
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'
const route = useRoute()

const event = ref(null)
onMounted(() => {
  EventService.getEvent(route.params.id)
    .then((response) => (event.value = response.data))
    .catch((error) => console.log(error))
})
</script>
