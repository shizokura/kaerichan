<template>
  <q-page class="flex flex-center">
    <HeartBackground />
    <div class="container text-center">
      <div class="heart"></div>
      <h1 class="text-h3 text-red">
        <TypewriterText
          text="Happy Valentine's Day, "
          :delay="100"
          :startTyping="true"
          @finished="startSecond = true"
        />
        <span class="text-weight-bold">
          <TypewriterText
            :text="name"
            :delay="100"
            :startTyping="startSecond"
            @finished="startThird = true"
          /> </span
        ><br />
        <span class="text-h4">
          <TypewriterText
            text="I love you! Lablab ko."
            :delay="100"
            :startTyping="startThird"
            @finished="startFourth = true"
          />
        </span>
      </h1>
      <span class="text-red" style="font-size: 1.5em">
        <TypewriterText
          text="Hehe pasensiya kung wala akong naready something for this day pero i want you to believe na importante ka sa akin and I want to spend the rest of my life with youuu. I love you so much! 😘"
          :delay="50"
          :startTyping="startFourth"
        />
      </span>
    </div>
  </q-page>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import HeartBackground from 'components/HeartBackground.vue'
import TypewriterText from 'components/TypewriterText.vue'

const name = ref('Erikaaa!')
const startSecond = ref(false)
const startThird = ref(false)
const startFourth = ref(false)
</script>

<style scoped>
.container {
  text-align: center;
  padding: 50px;
  max-width: 1000px;
  margin: auto;
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
