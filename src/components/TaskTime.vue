<script setup lang="ts">
import { ref, watch } from "vue"

// タイマー初期値作成
const INITIAL_TIME = '00:00:00'
const time = ref(INITIAL_TIME)

// 秒数時間設定
const HOUR_IN_SEC = 3600
const MIN_IN_SEC = 60

const timeToSec = (t: string): number => {
const [h,m,s] = t.split(':').map(e => parseInt(e))
   if (s === undefined) return 0
   return h * HOUR_IN_SEC + m * MIN_IN_SEC + s
 }

 const secToTime = (s: number): string => {
   return new Date(s * 1000).toISOString().substr(11, 8)
 }

 const sec = ref(0)
 const timerId = ref(0)

 const countDownInner = (): void => {
   sec.value--
   time.value = secToTime(sec.value)
 }
 const countDown = (): void => {
   timerId.value = setInterval(countDownInner, 1000)
 }

  const isTimerStopped = ref(true)
  const startTimer = (): void => {
   sec.value = timeToSec(time.value)
   if (sec.value <= 0) return
   isTimerStopped.value = false
   countDown()
 }

  const stopTimer = (): void => {
   clearInterval(timerId.value)
   isTimerStopped.value = true
 }

  const resetTimer = (): void => {
   stopTimer()
   time.value = INITIAL_TIME
 }

  watch(sec, (): void => {
   if (!isTimerStopped.value && sec.value > 0) return
   resetTimer()
 })
</script>

<template>
    <div class="timer">
      <div class="time">
         <input type="time" step="1" class="outline-none" v-model="time">
      </div>
      <div class="time-button">
      <button v-if="!isTimerStopped" class="purple-btn" type="button" @click="stopTimer()">Stop</button>
      <button v-else class="purple-btn" type="button" @click="startTimer()">Start</button>
      <button class="purple-btn" type="button" @click="resetTimer()">Reset</button>
      <button @click="deleteTweet(tweet.id)" type="checkbox" id="doneTweet">done</button>
      </div>
     </div>
</template>

<style>
.timer {
    margin: auto;
}
.outline-none {
    border: none;
    width: 300px;
    height: 80px;
    font-size: 50px;
}
</style>
