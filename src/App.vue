<template>
  <div class="container">
    <h2 :style="{ color: textColor }">
      Selamat Datang Di Web Saya  <hr>
      Masukkan 15 Huruf, Maka Warna Teks Ini Akan Berubah
    </h2>
    
    <div class="content">
      <div class="input-wrapper">
        <img :src="leftImageSource" class="left-image">
        <div class="input-container">
          <input type="text" v-model="inputText" class="input-field">
        </div>
      </div>
      <img :src="imageSource" :class="{ 'logo': true, 'vue': isVueLogo }" @click="toggleLogo">
    </div>
    <p class="message">{{ inputMessage }}</p>
    <p v-if="inputText" class="typed-text">Anda mengetik: {{ inputText }}</p>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const isVueLogo = ref(true);
const inputText = ref('');

const toggleLogo = () => {
  isVueLogo.value = !isVueLogo.value;
};

const textColor = computed(() => {
  return inputText.value.length > 15 ? 'red' : 'white';
});


const inputMessage = computed(() => {
  return inputText.value.length === 15 ? 'Anda telah mencapai 15 huruf' : '';
});

</script>

<style scoped>
.container {
  text-align: center;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #646cff;
  background-size: cover;
  background-position: center;
  background-color: rgba(255, 255, 255, 0.5); /* Mengatur opasitas latar belakang */
}

.content {
  margin-top: 20px;
}

.input-wrapper {
  display: flex;
  align-items: center;
}

.left-image {
  width: 100px;
  margin-right: 20px;
}

.input-container {
  margin: 0 auto; /* Memposisikan kolom input di tengah */
}

.input-field {
  width: 300px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #fff;
  color: #333;
}

.logo {
  height: 6em;
  padding: 1.5em;
  margin-top: 20px;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

.message {
  margin-top: 20px;
}

.typed-text {
  margin-top: 10px;
}
</style>
