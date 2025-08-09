<script setup>
import { ref } from 'vue';

const namaTamu = ref('');
const kehadiran = ref('');
const jumlahTamu = ref(1);
const pesan = ref('');

const formSubmitted = ref(false);

const handleSubmit = () => {
  console.log({
    nama: namaTamu.value,
    kehadiran: kehadiran.value,
    jumlah: jumlahTamu.value,
    pesan: pesan.value 
  });
  
  formSubmitted.value = true;
};
</script>

<template>
  <div class="rsvp-container" id="rsvp">
    <h2>Konfirmasi Kehadiran</h2>

    <form v-if="!formSubmitted" @submit.prevent="handleSubmit" class="rsvp-form">
      <div class="form-group">
        <label for="nama">Nama Anda</label>
        <input type="text" id="nama" v-model="namaTamu" required />
      </div>

      <div class="form-group">
        <label>Apakah Anda akan hadir?</label>
        <div class="radio-group">
          <label>
            <input 
              type="radio" 
              value="Hadir" 
              v-model="kehadiran" 
              name="status-kehadiran" 
              required> 
            Ya, saya akan hadir
          </label>
          <label>
            <input 
              type="radio" 
              value="Tidak Hadir" 
              v-model="kehadiran" 
              name="status-kehadiran"> 
            Maaf, tidak bisa hadir
          </label>
        </div>
      </div>
      
      <div class="form-group">
        <label for="jumlah">Jumlah Tamu (termasuk Anda)</label>
        <input type="number" id="jumlah" v-model="jumlahTamu" min="1" max="5" />
      </div>

      <div class="form-group">
        <label for="pesan">Pesan & Doa</label>
        <textarea id="pesan" v-model="pesan" rows="4"></textarea>
      </div>
      
      <button type="submit">Kirim Konfirmasi</button>
    </form>

    <div v-if="formSubmitted" class="thank-you-message">
      <h3>Terima kasih!</h3>
      <p>Konfirmasi Anda telah kami terima.</p>
    </div>
  </div>
</template>

<style scoped>
/* Style Anda sudah bagus, tidak perlu diubah */
.rsvp-container {
  padding: 40px 20px;
  background-color: #ffffff;
}

.rsvp-form {
  display: flex;
  flex-direction: column;
  gap: 20px;
  text-align: left;
}

.form-group {
  display: flex;
  flex-direction: column;
}

label {
  margin-bottom: 8px;
  font-weight: bold;
}

input[type="text"], input[type="number"], textarea {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 100%;
  box-sizing: border-box;
}

.radio-group label {
  display: block;
  margin-bottom: 5px;
  font-weight: normal;
}

button {
  padding: 12px 20px;
  background-color: #c59d5f;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
  font-weight: bold;
}

button:hover {
  background-color: #b38e54;
}

.thank-you-message {
  padding: 40px 20px;
  text-align: center;
}
</style>