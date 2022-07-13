<script setup lang="ts">
import { ref, defineEmits } from 'vue'

const inputtingDescription = ref<string>('')
// @clickを押した際にemitで親コンポへinputtingDescriptionの内容が送られる（post-taskという名前で)
const emit = defineEmits(['post-tweet'])
const postTweet = () => {
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

