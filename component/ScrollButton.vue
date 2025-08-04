<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const isScrolling = ref(false);
let scrollInterval = null;

const stopScroll = () => {
  if (scrollInterval) {
    clearInterval(scrollInterval);
    scrollInterval = null;
    isScrolling.value = false;
  }
};

const startScroll = () => {
  stopScroll(); 

  isScrolling.value = true;
  scrollInterval = setInterval(() => {
    const atBottom = window.innerHeight + window.scrollY >= document.body.offsetHeight - 5;

    if (atBottom) {
      stopScroll();
    } else {
      window.scrollBy(0, 500);
    }
  }, 100);
};

const toggleAutoScroll = () => {
  if (isScrolling.value) {
    stopScroll();
  } else {
    startScroll();
  }
};


onMounted(() => {
  window.addEventListener('wheel', stopScroll);
  window.addEventListener('touchmove', stopScroll); 
});

onUnmounted(() => {
  window.removeEventListener('wheel', stopScroll);
  window.removeEventListener('touchmove', stopScroll);
  stopScroll();
});
</script>

<template>
  <button @click="toggleAutoScroll" class="scroll-button" title="Gulir Otomatis">
    <img v-if="isScrolling" src="/src/icon/pause.svg" alt="Pause Scroll">
    <img v-else src="/src/icon/play.svg" alt="Auto Scroll">
  </button>
</template>

<style scoped>
.scroll-button {
  position: fixed;
  bottom: 90px;
  right: 20px;
  
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.9);
  border: 1px solid #eee;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  cursor: pointer;
  
  display: flex;
  justify-content: center;
  align-items: center;
  
  z-index: 99;
  transition: transform 0.2s ease;
}

.scroll-button:hover {
  transform: scale(1.1);
}

.scroll-button img {
  width: 24px;
  height: 24px;
}
</style>