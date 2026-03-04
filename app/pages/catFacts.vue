<!--Chloe Larsen u25004141-->
<script setup>
import { ref } from 'vue';

// Add a timestamp to force the browser to fetch a new image
const timestamp = ref(Date.now());
const catImageUrl = computed(() => `https://cataas.com/cat?${timestamp.value}`);

const refreshCat = () => {
  timestamp.value = Date.now();
};
</script>

<template>
  <div class="cat-container">
    <h3>😺 Random Cat</h3>
    <img :src="catImageUrl" alt="Random cat" class="cat-image" />
    <button @click="refreshCat">Get New Cat</button>
  </div>
</template>

<style>
.cat-image {
  width: 100%;
  max-width: 600px;
  height: auto;
  max-height: 400px;
  object-fit: cover;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  display: block;
  margin: 0 auto;
}

.cat-container {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1rem;
  background-color: #f9f9f9;
  border-radius: 12px;
  margin: 1rem 0;
}
</style>
