<script setup lang="ts">
import { ref } from 'vue';
import 'v-calendar/dist/style.css';
import { Calendar, DatePicker } from 'v-calendar';

const date = ref<number>()

</script>

<template>
  <DatePicker v-model="date"></DatePicker>
</template>

<style>

</style>
