<script setup lang="ts">
import { onMounted, onUnmounted, ref } from 'vue'

const images = [
  './assets/recommended.jpg',
  './assets/wagyu.png',
  './assets/tasty.gif',
]

const currentIndex = ref(0)
let intervalId: number | null = null

onMounted(() => {
  intervalId = window.setInterval(() => {
    currentIndex.value = (currentIndex.value + 1) % images.length
  }, 3000)
})

onUnmounted(() => {
  if (intervalId) clearInterval(intervalId)
})
</script>

<template>
  <div class="root">
    <div class="wrapper wrapper-text">
      <img class="takumi-logo" src="./assets/takumi-logo.png" alt="Logo" />
      <p class="title">
        <span class="title-jpn">お誕生日おめでとう</span>
        <span>Otanjoubi omedetou, Sensei Jonas!</span>
      </p>
      <p class="description">Ich überreiche dir hiermit feierlich einen Gutschein für das beste Wagyu bei <a href="https://wagyu-idaten.com/#top" target="_blank">Takumi's Jubako Wagyu Idaten</a>!</p>
      <p class="description">🐂 🥩 🍚 🍣 🍶</p>
    </div>
    <div class="wrapper">
      <img class="pic" src="./assets/recommended.jpg" alt="Tasty" />
      <img class="pic" src="./assets/tasty.gif" alt="Tasty" />
      <img class="pic" src="./assets/wagyu.jpg" alt="Tasty" />
    </div>
  </div>
</template>

<style scoped>
.root {
  width: 100dvw;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  padding: 6rem 0 0 0;
  
  .wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    max-width: 650px;

    .title {
      font-size: 2rem;
      text-align: center;
      padding: 0;
      margin: 0;
      margin-bottom: 2rem;
    }

    .title-jpn {
      padding: 0;
      margin: 0;
    }

    .description {
      text-align: center;
      padding: 0;
      margin: 0;
    }
    
    .takumi-logo {
      width: 100px;
      margin-bottom: 1rem;
    }

    .pic {
      width: 100%;
    }
  }

  .wrapper-text {
    padding: 0 1rem;
    margin-bottom: 6rem;
  }
}
</style>
