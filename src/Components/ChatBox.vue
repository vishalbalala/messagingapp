<script setup>
import { ref, defineEmits } from 'vue'

const text = ref('')
const emit = defineEmits(['submit'])

const onSubmit = (event) => {
  event.preventDefault()
  emit('submit', text.value)
  text.value = ''
}
</script>

<template>
  <form class="flex bg-white w-full" @submit="onSubmit($event)">
    <textarea class="flex-1 mr-3" v-model="text" placeholder="Write a message" type="text" />
    <button :disabled="text === ''">Send</button>
  </form>
</template>
