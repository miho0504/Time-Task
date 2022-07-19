<script setup lang="ts">
import { ref } from 'vue';
import 'v-calendar/dist/style.css';
import { Calendar, DatePicker } from 'v-calendar';

const date = ref<number>()
const inputEvent = ref<string>("")

</script>

<template>
  <DatePicker class="calendar" @input="inputEvent" v-model="date"></DatePicker>
</template>

<style>
.calendar {
  width: 600px;
  height: 400px;
}
</style>
