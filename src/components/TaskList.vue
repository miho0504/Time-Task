<script setup lang="ts">
import { defineProps, ref } from 'vue';
import TaskTime from './TaskTime.vue'

const dialogIsvisible = ref(false)
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

// モーダル
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
      <div class="container">
        <button @click="toggleModal">Time</button>
      </div>
      <TaskTime />

        <modal v-if="dialogIsVisible">
        <p>this is a test modal</p>
        <button @click="toggleModal">close</button>
      </modal>
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
}

/* モーダル */

.modal-enter-from {
  opacity: 0;
  transition: translate(0);
}

.modal-enter-active {
  animation: modal 0.3s ease-out; 
}

/* アニメーション */
@keyframes modal {
    from {
       opacity: 0;
       transform: translateY(-50px) scale(0.9); 
    }

    to {
        opacity: 1;
        transform: translateY(0) scale(1); 

    }
}
</style>