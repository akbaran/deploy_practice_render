<script setup>
/*
import { ref } from 'vue'
import { RouterLink } from 'vue-router' // used to create a state, used for creating event data
*/

defineProps({
  event: { //the parent, EventListView.vue, is going to feed each event to this component for display
    type: Object,
    required: true
  }
})


</script>

<template>
  <RouterLink class="event-link" v-bind:to="{ name: 'event-details', params: { id: event.id } }">
    <div class="event-card">
      <!--  event data  -->
      <!-- start printing information from the object passed to ref() -->
      <h2>{{ event.title }}</h2>
      <span>@{{ event.time }} on {{ event.date }}</span>
    </div>
  </RouterLink>
</template>

<style scoped>
.event-card {
  padding: 20px;
  width: 250px;
  cursor: pointer;
  border: 1px solid #181818;
  margin-bottom: 18px;
}

.event-card:hover {
  transform: scale(1.01);
  box-shadow: 0px 3px 12px 0px rgba(0,0,0,0.2);
}

.event-link {
  color: #2c3e50;
  text-decoration: none;
}
</style>
