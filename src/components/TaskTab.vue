<script setup lang="ts">



</script>

<template>
     <div class="tweet-list-container">
      <div class="tweet-list-innner">
        <li v-for="tweet in tweets" :key="tweet.id" class="tweets-list">
        <input type="checkbox" id="checkbox" v-model="checked" />
        <label for="checkbox">{{ checked }}</label>
      <span>{{ tweet.description }}</span>
      <button @click="deleteTweet(tweet.id)" class="delete-button">delete</button>
      <button @click="deleteTweet(tweet.id)" class="delete-button">Time</button>
    </li>
      </div>
    </div>
</template>

<style scoped>
</style>