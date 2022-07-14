<script setup lang="ts">

</script>


<template>
  <div class="backdrop">
    <transition name="modal">
      <dialog open v-if="open" class="dialog">
      <slot></slot>
      </dialog>
    </transition>
  </div>
</template>  


<style scoped>

/* モーダル */

.backdrop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    z-index: 10;
    background-color: rgba(0, 0, 0, 0.077);
}

.dialog {
    position: fixed;
    top: 30vh;
    width: 30rem;
    left: calc(50% - 15rem);
    margin: 0;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.25);
    border-radius: 12px;
    padding: 1rem;
    background-color: white;
    z-index: 100;
    border: none;
}

</style>