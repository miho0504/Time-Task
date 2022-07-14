<script setup lang="ts">
import { defineProps, } from 'vue';
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
    <div class="tweet-list-container">
      <div class="tweet-list-innner">
        <li v-for="tweet in tweets" :key="tweet.id" class="tweets-list">
        <input type="checkbox" id="doneTweet" v-model="doneTweet" />
      <span>{{ tweet.description }}</span>
      <button @click="deleteTweet(tweet.id)" class="delete-button">delete</button>
      <button @click="deleteTweet(tweet.id)" class="delete-button">Time</button>
    </li>
      </div>
    </div>
</template>

<style scoped>

.tweet-list-container {
    margin-top: 50px;
    justify-content: space-between;
    
}

.tweet-list-innner {    
    padding-left: 30px;
    justify-content:space-between;
}

.delete-button {
    background-color: rgb(190, 92, 92);
    font-size: 20px;
    margin-left: 10px;
    
}

span {
    margin-left: 10px;
}

li {
    list-style: none;
    margin: 30px;
    height: 50px;
    font-size: 25px;
        background-color: aquamarine;
}
</style>