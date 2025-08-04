<script setup>
import { ref, onMounted } from 'vue';

const props = {
  mempelaiPria: 'Skibidi',
  mempelaiWanita: 'Sigma'
};

const displayedName = ref('');
const isTypingPria = ref(true);

onMounted(() => {
  let index = 0;
  displayedName.value = ' '; 

  const typingInterval = setInterval(() => {
    if (isTypingPria.value) {
      if (index < props.mempelaiPria.length) {
        displayedName.value += props.mempelaiPria[index];
        index++;
      } else {
        isTypingPria.value = false;
        index = 0;
        displayedName.value += ' & ';
      }
    } else {
      if (index < props.mempelaiWanita.length) {
        displayedName.value += props.mempelaiWanita[index];
        index++;
      } else {
        displayedName.value = displayedName.value.trim(); 
        clearInterval(typingInterval);
      }
    }
  }, 150);
});
</script>

<template>
  <div class="hero-container" id="hero">
    <div class="corner-decoration top-left"></div>
    <div class="corner-decoration bottom-right"></div>
    
    <div class="hero-content">
      <h4>The Wedding Of</h4>
      <h1>{{ displayedName }}<span v-if="displayedName.includes(' ')" class="cursor"></span></h1>
      <p>Kami dengan tulus mengundang Anda ke dalam perayaan cinta kami.</p>
    </div>
  </div>
</template>

<style scoped>
.hero-container {
  position: relative; 
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: white;
  overflow: hidden; 
  
  background-image: url('/src/image/bg.jpeg'); 
  background-size: cover;
  background-position: center;
}

.hero-container::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.4);
  z-index: 1;
}

.hero-content {
  position: relative;
  z-index: 2;
  padding: 20px;
  animation: fadeInTeks 2s ease-out;
}

h4 {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.5rem;
  font-weight: 400;
  margin: 0;
}

h1 {
  font-family: 'Dancing Script', cursive;
  font-size: 4rem;
  margin: 10px 0;
  color: #FFFFFF;
  text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.7);
  min-height: 80px; 
}

p {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.1rem;
  margin-top: 15px;
}

.corner-decoration {
  position: absolute;
  width: 150px;
  height: 150px;
  background-image: url('/src/image/dec.png');
  background-size: contain;
  background-repeat: no-repeat;
  z-index: 2;
  opacity: 0.8;
}

.top-left {
  top: 20px;
  left: 20px;
}

.bottom-right {
  bottom: 20px;
  right: 20px;
  transform: rotate(180deg);
}

.cursor {
  display: inline-block;
  background-color: white;
  width: 3px;
  margin-left: 8px;
  animation: blink 1s infinite;
}

@keyframes blink {
  50% { opacity: 0; }
}

@keyframes fadeInTeks {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

@media (max-width: 480px) {
  h1 {
    font-size: 3rem;
  }
  .corner-decoration {
    width: 500px;
    height: 150px;
  }
}
</style>