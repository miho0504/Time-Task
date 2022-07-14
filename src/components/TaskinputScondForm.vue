<script setup lang="ts">
import { onMounted, ref, defineEmits } from 'vue'
import axios from 'axios';

const inputtingDescription = ref<string>('')
// @clickを押した際にemitで親コンポへinputtingDescriptionの内容が送られる（post-taskという名前で)
const emit = defineEmits(['post-tweet'])

// firebase
onMounted(async () => {
  const data = await axios.get('https://my-task-fabeb-default-rtdb.firebaseio.com/tasklist.json')
})

const postTweet = (e: Event) => {
      axios.post('https://my-task-fabeb-default-rtdb.firebaseio.com/tasklist.json',{
      description: inputtingDescription.value,
  })
    emit('post-tweet', inputtingDescription.value)
}

</script>

<template>
<div class="form-container">
    <input v-model="inputtingDescription">
    <button class="save-button" @click="postTweet">post</button>
</div>
</template>

<style scoped>
</style>

