<template>
  <span>{{ displayText }}</span>
</template>

<script setup lang="ts">
import { ref, onMounted, watchEffect } from 'vue'

const props = defineProps<{
  text: string
  delay?: number
  startTyping?: boolean
}>()

const emit = defineEmits(['finished'])
const displayText = ref('')

onMounted(() => {
  if (props.startTyping) {
    startAnimation()
  }
})

const startAnimation = () => {
  let currentIndex = 0
  displayText.value = ''

  const interval = setInterval(() => {
    if (currentIndex < props.text.length) {
      displayText.value = props.text.substring(0, currentIndex + 1)
      currentIndex++
    } else {
      clearInterval(interval)
      emit('finished')
    }
  }, props.delay || 100)
}

watchEffect(() => {
  if (props.startTyping) {
    startAnimation()
  }
})
</script>
