<script setup>
import EventCard from '@/components/EventCard.vue'
import { ref, onMounted } from 'vue'
import EventService from '@/services/EventServices.js'

const events = ref(null)

onMounted(() => {
  EventService.getEvents()
    .then( (respond) => {
      events.value = respond.data

    } ).catch((error) => {
      console.log(error)
    })
})
</script>

<template>
  <h1>Events for Good</h1>
  <div class="events">
    <EventCard v-for="event in events" v-bind:key="event.id" v-bind:event="event"/>
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>