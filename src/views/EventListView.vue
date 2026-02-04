<script setup>
import EventCard from '@/components/EventCard.vue'
import { onMounted, ref } from 'vue'
// ~~import axios from 'axios'~~
import EventSevice from '@/services/EventSevice'

const events = ref(null)
onMounted(() => {
  EventSevice.getEvents()
    .then((response) => {
      events.value = response.data
    })
    .catch((error) => {
      console.log(error)
    })
})
</script>

<template>
  <h1>Events for Good</h1>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>
<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
