<script setup lang="ts">
import { defineProps } from 'vue';
type Tweet = {
    id: number,
    description: string,
}
type Props = {
    tweets: Tweet[]
    deleteTweet: (id: number) => void
}
defineProps<Props>()

</script>

<template>
    <li v-for="tweet in tweets" :key="tweet.id" class="tweets-list">
    <input @click="deleteTweet(tweet.id)" type="checkbox" id="checkbox" v-model="checked" />
      <span>{{ tweet.description }}</span>
      <button @click="deleteTweet(tweet.id)" class="delete-button">delete</button>
      <button @click="deleteTweet(tweet.id)" class="delete-button">Time</button>
    </li>
</template>

<style scoped>
</style>