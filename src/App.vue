<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import { ref, computed } from 'vue'
import Task from './components/Task.vue'
import TaskTab from './components/TaskTab.vue'

const isFirstTab = ref(true)
const updateTab = (isFirst: boolean) => {
  isFirstTab.value = isFirst
}

const currentComponent = computed(() =>{
  switch (isFirstTab.value){
    case true:
      return Task
    case false:
      return TaskTab
    default:
      return Task
  }
})

</script>

<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <div class="tab-changer">
    <button @click="updateTab(true)">Tab 1</button>
    <button @click="updateTab(false)">Tab 2</button>
  </div>
  <div class="tab-contents">
    <component :is="currentComponent"></component>
  </div>
  <!-- <HelloWorld /> -->
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
