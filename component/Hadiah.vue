<script setup>
import { ref } from 'vue';

const dataRekening = {
  pria: {
    bank: 'BCA',
    nama: 'Skibidi',
    nomor: '1234567890'
  },
  wanita: {
    bank: 'BRI',
    nama: 'Sigmawati',
    nomor: '0987654321'
  }
};

const copyStatusPria = ref('Salin Nomor');
const copyStatusWanita = ref('Salin Nomor');

// --- FUNGSI YANG DIPERBAIKI ---
const copyToClipboard = (text, target) => {
  const updateStatus = (statusRef) => {
    statusRef.value = 'Berhasil Disalin!';
    setTimeout(() => {
      statusRef.value = 'Salin Nomor';
    }, 2000);
  };

  if (navigator.clipboard) {
    navigator.clipboard.writeText(text).then(() => {
      updateStatus(target === 'pria' ? copyStatusPria : copyStatusWanita);
    }).catch(err => {
      console.error('Gagal menyalin (API Modern): ', err);
    });
  } else {
    const textArea = document.createElement("textarea");
    textArea.value = text;
    textArea.style.position = "fixed"; // Jauhkan dari pandangan
    textArea.style.left = "-9999px";
    document.body.appendChild(textArea);
    textArea.focus();
    textArea.select();
    try {
      document.execCommand('copy');
      updateStatus(target === 'pria' ? copyStatusPria : copyStatusWanita);
    } catch (err) {
      console.error('Gagal menyalin (Metode Lama): ', err);
    }
    document.body.removeChild(textArea);
  }
};
</script>

<template>
  <div class="gift-container" id="hadiah">
    <h2>Kirim Hadiah</h2>
    <p class="intro-text">
      Doa restu Anda merupakan karunia yang sangat berarti bagi kami. Namun jika memberi adalah ungkapan tanda kasih, Anda dapat memberi kado secara cashless.
    </p>

    <div class="gift-options">
      <div class="gift-card">
        <h3 class="bank-name">{{ dataRekening.pria.bank }}</h3>
        <p class="account-number">{{ dataRekening.pria.nomor }}</p>
        <p class="account-name">a.n. {{ dataRekening.pria.nama }}</p>
        <button 
          @click="copyToClipboard(dataRekening.pria.nomor, 'pria')" 
          :class="{ copied: copyStatusPria.includes('Berhasil') }"
          class="copy-button">
          {{ copyStatusPria }}
        </button>
      </div>

      <div class="gift-card">
        <h3 class="bank-name">{{ dataRekening.wanita.bank }}</h3>
        <p class="account-number">{{ dataRekening.wanita.nomor }}</p>
        <p class="account-name">a.n. {{ dataRekening.wanita.nama }}</p>
        <button 
          @click="copyToClipboard(dataRekening.wanita.nomor, 'wanita')"
          :class="{ copied: copyStatusWanita.includes('Berhasil') }"
          class="copy-button">
          {{ copyStatusWanita }}
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.gift-container {
  padding: 60px 20px;
  text-align: center;
  background-color: var(--color-bg-medium, #f7f0e8);
}

.intro-text {
  max-width: 600px;
  margin: 0 auto 40px auto;
  font-size: 1.1rem;
  line-height: 1.7;
}

.gift-options {
  display: flex;
  justify-content: center;
  gap: 20px;
  flex-wrap: wrap; /* Agar responsif di layar kecil */
}

.gift-card {
  background-color: #ffffff;
  border-radius: 12px;
  padding: 30px;
  width: 280px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  border: 1px solid #e0d9d0;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.bank-name {
  font-family: var(--font-primary, 'Cormorant Garamond');
  font-weight: 700;
  font-size: 1.5rem;
  color: var(--color-dark, #5d5d5d);
  margin: 0 0 10px 0;
}

.account-number {
  font-size: 1.4rem;
  font-weight: bold;
  color: var(--color-gold, #c59d5f);
  margin: 5px 0;
  letter-spacing: 1px;
}

.account-name {
  font-size: 1rem;
  margin-top: 5px;
  margin-bottom: 25px;
}

.copy-button {
  padding: 10px 20px;
  border: 1px solid var(--color-gold, #c59d5f);
  background-color: var(--color-gold, #c59d5f);
  color: white;
  border-radius: 20px;
  cursor: pointer;
  font-weight: bold;
  transition: all 0.3s ease;
}

.copy-button:hover {
  background-color: #b38e54;
  border-color: #b38e54;
}

.copy-button.copied {
    background-color: #28a745; /* Warna hijau sukses */
    border-color: #28a745;
}

.qris-section {
    margin-top: 50px;
}

.qris-image {
    width: 200px;
    height: auto;
    margin-top: 15px;
    border-radius: 8px;
    border: 1px solid #ddd;
}
</style>