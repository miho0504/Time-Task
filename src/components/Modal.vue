<script setup lang="ts">
import { defineProps, ref } from 'vue';
import TaskTime from './TaskTime.vue';

const dialogIsvisible = ref(false)

const toggleModal = () => {
  dialogIsvisible.value = !dialogIsvisible.value
}


</script>

<template>
      <!-- <dialog open v-if="open" class="dialog"> -->
      <div class="dialog">
      <TaskTime />
      </div>
       <slot></slot>
      <!-- </dialog> -->
  <div class="backdrop">
      <!-- ボックス内容 -->
  </div>
</template>  


<style scoped>

/* モーダル */
/* 後ろの黒い背景 */
.backdrop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    z-index: 10;
    background-color: rgba(0, 0, 0, 0.077);
}

/* ダイアログボックス */
.dialog {
    position: fixed;
    top: 30vh;
    width: 30rem;
    height: 20rem;
    left: calc(50% - 15rem);
    margin: 0;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.25);
    border-radius: 12px;
    padding: 1rem;
    background-color: white;
    z-index: 999;
    border: none;
}

/* モーダル */

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