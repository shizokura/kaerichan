<template>
  <q-page class="flex flex-center">
    <HeartBackground />
    <div class="container text-center">
      <div class="heart"></div>
      <h1 class="text-h3 text-red">
        Happy Valentine's Day, <span class="text-weight-bold">{{ name }}</span
        >! <br />
        <span class="text-h4">I love you! Lablab ko</span>
      </h1>
    </div>
  </q-page>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import HeartBackground from 'components/HeartBackground.vue'
const name = ref('Erikaaa')
</script>

<style scoped>
.container {
  text-align: center;
  padding: 0 50px;
}

.heart {
  width: 100px;
  height: 90px;
  position: relative;
  animation: beat 1.5s infinite;
  margin: 20px auto;
}

.heart::before,
.heart::after {
  content: '';
  position: absolute;
  top: 0;
  width: 52px;
  height: 80px;
  background: #d32f2f;
  border-radius: 50px 50px 0 0;
  transform: rotate(-45deg);
  transform-origin: 0 100%;
}

.heart::after {
  left: 0px;
  transform: rotate(45deg);
  transform-origin: 100% 100%;
}

@keyframes beat {
  0%,
  100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.1);
  }
}
</style>
