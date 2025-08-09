
<script setup>
import { ref, onMounted } from 'vue'

const props = defineProps({
  namaTamu: String
});

const mempelaiPria = "Sigma"
const mempelaiWanita = "Skibidi"

const emit = defineEmits(['open']);

const displayedName = ref('');
let index = 0;

onMounted(() => {
  const typingInterval = setInterval(() => {
    if (index < props.namaTamu.length) {
      displayedName.value += props.namaTamu[index];
      index++;
    } else {
      clearInterval(typingInterval);
    }
  }, 150);
});
</script>

<template>
  <div class="cover-container">
    <div class="content">
      <h4>The Wedding Of</h4>
      <h1>{{ mempelaiPria }} & {{ mempelaiWanita }}</h1>
      <p>Kepada Yth. Bapak/Ibu/Saudara/i</p>
      <h2 class="guest-name">
        {{ displayedName }}<span class="cursor"></span>
      </h2>
      <button @click="emit('open')">Buka Undangan</button>
    </div>
  </div>
</template>

<style scoped>
.cover-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: #fdfaf6 url('/src/image/bg.png') no-repeat center center; 
  background-size: cover;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  z-index: 100;
  color: white;
}

.cover-container::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
}

.content {
  position: relative; 
  z-index: 1;
  padding: 20px;
}

.guest-name {
  font-size: 2.5rem;
  margin: 10px 0 30px 0;
  font-family: 'Dancing Script', cursive;
}

button {
  padding: 10px 30px;
  font-size: 1rem;
  cursor: pointer;
  border-radius: 20px;
  border: 1px solid white;
  background-color: rgba(255, 255, 255, 0.2);
  color: white;
  transition: background-color 0.3s;
}

button:hover {
  background-color: rgba(255, 255, 255, 0.4);
}
</style>