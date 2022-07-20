<script setup lang="ts">
import { ref, computed } from 'vue'
import TaskinputForm from './TaskinputForm.vue';
import TaskList from './TaskList.vue';

const tweets = ref([{ id: 0, description: 'hello'}])
const postTweet = (description: string ) => {
  const tweet = { id: Math.random(), description }
  tweets.value.push(tweet)
}
const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter(t => t.id !== id)
}

const title = ref<string>("Tasks still due")

</script>

<template>
<div class="container">
  <TaskinputForm @post-tweet="postTweet"/>
  <h2>{{ title }}</h2>
  <div class="tweets-container">
    <p v-if="tweets.length <= 0">complete！！！</p>
    <ul>
      <TaskList :tweets="tweets" :delete-tweet="deleteTweet"/>
    </ul>
  </div>
</div>
</template>

<style scoped>

.container {
    width: 500px;
    margin: auto;
}
</style>
