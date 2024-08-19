<script setup>
import EventCard from '../components/EventCard.vue'
</script>

<template>
  <main class="events">
    <EventCard />
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
