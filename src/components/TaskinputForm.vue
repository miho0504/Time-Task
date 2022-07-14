<script setup lang="ts">
import { onMounted, ref, defineEmits, computed } from 'vue'
import axios from 'axios';
import Datepicker from '@vuepic/vue-datepicker';
import '@vuepic/vue-datepicker/dist/main.css'

// 日付関連
const date = ref();

const inputtingDate = ref<number>()
const inputtingDescription = ref<string>('')

// @clickを押した際にemitで親コンポへinputtingDescriptionの内容が送られる（post-taskという名前で)
const emit = defineEmits(['post-tweet'])

// firebase関連
onMounted(async () => {
  const data = await axios.get('https://my-task-fabeb-default-rtdb.firebaseio.com/tasklist.json')
})

const postTweet = (e: Event) => {
      axios.post('https://my-task-fabeb-default-rtdb.firebaseio.com/tasklist.json',{
      description: inputtingDescription.value,
      date: inputtingDate.value,
  })
    emit('post-tweet', inputtingDescription.value)
}

// バリテーション関連 computed 計算 
const nameLengthLimit = 15
const inputLengthLimit = 0

const isValidName = computed(()=> {
    if (inputtingDescription.value.length >= nameLengthLimit ) {
      return false
    } else {
      return true
    }
})

// const isValid = computed(()=> {
//     if (inputtingDescription.value.length == inputLengthLimit &&
//         inputtingDate.value == inputLengthLimit ) {
//       return false
//     } else {
//       return true
//     }
// })

const color = computed(() => {
    return isValidName.value? 'white' : 'tomato'
})

</script>

<template>
<div class="form-container">
    <Datepicker v-model="inputtingDate"></Datepicker>
    <span v-if="!isValidName">{{ nameLengthLimit }} 文字以内</span>
    <input class="input-name" v-model="inputtingDescription">
    <button class="save-button" @click="postTweet">post</button>
</div>
</template>

<style scoped>

.input-name {
    background-color: v-bind(color);
}
</style>

