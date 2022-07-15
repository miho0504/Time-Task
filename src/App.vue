<script setup lang="ts">
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

const title = ref<string>("Time-Task-Calendar")

</script>

<template>
  <img alt="logo" src="./assets/icon.png"/>
  <h1>{{ title }}</h1>
  <div class="tab-changer">
    <button @click="updateTab(true)">today</button>
    <button @click="updateTab(false)">end day</button>
  </div>
  <div class="tab-contents">
    <component :is="currentComponent"></component>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

h1 {
  font-size: 40px;
}

img {
  width: 30%;
  height: 30%;;
}

.tab-changer {
  width: 100%;
}

.tab-changer button {
  width: 280px;
  height: 40px;
  font-size: 20px;
  background-color: white;
}
</style>
