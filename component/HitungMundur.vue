<script setup>
import { ref, onMounted } from 'vue';

const targetDate = new Date("2025-09-14T09:00:00").getTime();

const hari = ref(0);
const jam = ref(0);
const menit = ref(0);
const detik = ref(0);

const updateCountdown = () => {
  const now = new Date().getTime();
  const jarak = targetDate - now;

  if (jarak < 0) {
    hari.value = 0;
    jam.value = 0;
    menit.value = 0;
    detik.value = 0;
    return;
  }

  hari.value = Math.floor(jarak / (1000 * 60 * 60 * 24));
  jam.value = Math.floor((jarak % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
  menit.value = Math.floor((jarak % (1000 * 60 * 60)) / (1000 * 60));
  detik.value = Math.floor((jarak % (1000 * 60)) / 1000);
};

onMounted(() => {
  setInterval(updateCountdown, 1000);
});
</script>

<template>
  <div class="countdown-container">
    <h2>Menuju Hari Bahagia</h2>
    <div class="timer">
      <div class="time-box">
        <div class="time-value">{{ hari }}</div>
        <div class="time-label">Hari</div>
      </div>
      <div class="time-box">
        <div class="time-value">{{ jam }}</div>
        <div class="time-label">Jam</div>
      </div>
      <div class="time-box">
        <div class="time-value">{{ menit }}</div>
        <div class="time-label">Menit</div>
      </div>
      <div class="time-box">
        <div class="time-value">{{ detik }}</div>
        <div class="time-label">Detik</div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.countdown-container {
  padding: 40px 20px;
  background-color: #f7f0e8;
}

h2 {
  margin-bottom: 30px;
}

.timer {
  display: flex;
  justify-content: space-around;
  text-align: center;
}

.time-box {
  background-color: white;
  padding: 10px;
  border-radius: 8px;
  width: 70px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.05);
}

.time-value {
  font-size: 2rem;
  font-weight: bold;
  color: #c59d5f;
}

.time-label {
  font-size: 0.8rem;
  color: #5d5d5d;
}
</style>