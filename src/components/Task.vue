<script setup lang="ts">
import { ref, computed } from 'vue'
import TaskinputForm from './TaskinputForm.vue';
import TaskList from './TaskList.vue';

// 入力関連
const tweets = ref([{ id: 0, description: 'hello'}])
const postTweet = (description: string) => {
  const tweet = { id: Math.random(), description }
  tweets.value.push(tweet)
}
const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter(t => t.id !== id)
}
const title = ref<string>("Time-Task")
// defineProps<{ msg: string }>()

</script>

<template>
<h1>{{ title }}</h1>
<div class="container">
  <!-- 子コンポーネントでボタンが押されたり、テキストボックスの変更などが発生したときに親コンポーネントに伝える -->
  <TaskinputForm @post-tweet="postTweet"/>
  <div class="tweets-container">
    <p v-if="tweets.length <= 0">No tweets have been addded</p>
    <ul>
      <TaskList :tweets="tweets" :delete-tweet="deleteTweet"/>
    </ul>
  </div>
</div>
</template>

<style scoped>
</style>
