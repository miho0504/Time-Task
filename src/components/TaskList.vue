<script setup lang="ts">
import { defineProps, ref,onMounted } from 'vue';
import TaskTime from './TaskTime.vue';
import Modal from './Modal.vue';

const date = ref();
  
const dialogIsvisible = ref(false)
const calendarIsvisible = ref(false)
const today = new Date();


type Tweet = {
    id: number,
    description: string,
}
type Props = {
    tweets: Tweet[]
    deleteTweet: (id: number) => void
}

defineProps<Props>()

// モーダル ボタンを押すとdialogIsvisibleが変更される
const toggleModal = () => {
  dialogIsvisible.value = !dialogIsvisible.value
}

</script>

<template>
    <div class="tweet-list-container">
      <div class="tweet-list-innner">
      <li v-for="tweet in tweets" :key="tweet.id" class="tweets-list">
      <span>{{ tweet.description }}</span>
      <button @click="deleteTweet(tweet.id)" type="checkbox" id="doneTweet">done</button>
      <button @click="toggleModal">Time</button>
    </li>
      </div>
    </div>

      <Modal v-if="dialogIsvisible"></Modal>
      <div class="calendar-button">
        <button @click="calendarModal">か</button>
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
}

/* .modal-container {
  border: solid 3px #000000;
} */

.modal-enter-from {
  opacity: 0;
  transition: translate(0);
}

</style>