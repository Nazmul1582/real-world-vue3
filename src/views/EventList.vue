<script setup>
import { ref, onMounted } from 'vue'
import EventCard from '../components/EventCard.vue'
import axios from 'axios';
const events = ref(null)
onMounted(() => {
  // fetch api call ============
  // fetch('/db.json')
  //   .then((response) => response.json())
  //   .then((data) => {
  //     events.value = data.events
  //   })
  //   .catch((error) => console.log(error))

  // api call using Axios
  axios
    .get('/db.json')
    .then((data) => events.value = data.data.events)
    .catch((error) => console.log(error))

})
</script>

<template>
  <main class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </main>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
