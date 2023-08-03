<script setup lang="ts">
import { ref } from 'vue';

const dragState = ref("null");
const isEnter = ref();

const handleDragEnter = (e: Event) => {
  dragState.value = "handleDragEnter";
  isEnter.value = true;
  e.preventDefault();
}

const handleDragLeave = (e: Event) => {
  dragState.value = "handleDragLeave";
  isEnter.value = false;
  e.preventDefault();
}

const handleDrop = (e) => {
  e.preventDefault();
}
</script>

<template>
  <form action="#" method="post">
    <div 
      :class="`drop-area ${ isEnter ? 'isEnter' : '' }`"
      @dragenter="handleDragEnter"
      @dragleave="handleDragLeave"
      @drop="handleDrop"
      @dragover.prevent
    >
      <p>Image file drop here.</p>
      <p>{{ dragState }}</p>
    </div>
    <input type="file" hidden />
  </form>
</template>
