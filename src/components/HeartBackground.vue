<template>
  <div class="hearts-container">
    <div v-for="n in 20" :key="n" class="heart-float" :style="randomStyle()"></div>
  </div>
</template>

<script setup lang="ts">
const randomStyle = () => {
  return {
    left: Math.random() * 100 + 'vw',
    animationDuration: 3 + Math.random() * 7 + 's',
    animationDelay: Math.random() * 5 + 's',
  }
}
</script>

<style scoped>
.hearts-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
  z-index: -1;
  pointer-events: none;
}

.heart-float {
  position: fixed;
  width: 20px;
  height: 20px;
  background: rgb(211, 47, 47);
  transform: rotate(45deg);
  animation: floatUp linear infinite;
  bottom: -100px;
}

.heart-float:before,
.heart-float:after {
  content: '';
  width: 20px;
  height: 20px;
  background: rgb(211, 47, 47);
  border-radius: 50%;
  position: absolute;
}

.heart-float:before {
  top: -10px;
  left: 0;
}

.heart-float:after {
  left: -10px;
  top: 0;
}

@keyframes floatUp {
  0% {
    transform: translateY(0) rotate(45deg);
    opacity: 1;
  }
  100% {
    transform: translateY(-100vh) rotate(45deg);
    opacity: 0;
  }
}
</style>
