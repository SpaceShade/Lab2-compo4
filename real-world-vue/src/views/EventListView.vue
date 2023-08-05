<script setup lang="ts">
import EventCard from '../components/EventCard.vue'
import type { EventItem } from '@/type';
import axios from 'axios'

import {ref, type Ref} from 'vue'
const events : Ref<Array<EventItem>> = ref([])
axios.get<EventItem[]>('http://localhost:3004/events')
.then((response) =>{
  events.value = response.data
})
</script>

<template>
  <main class="events">
    <h1>Events for Good</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event"></EventCard>
  </main>
</template>

<style scoped>
.events{
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
