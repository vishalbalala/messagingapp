<script setup>
import { toRefs } from 'vue'
const props = defineProps({
  message: {
    type: Object,
    default: () => ({})
  },
  isMine: {
    type: Boolean,
    default: false
  }
})
const { message } = toRefs(props)
</script>

<template>
  <div class="flex items-end mb-5" :class="{ 'flex-row-reverse': isMine }">
    <img src="../assets/user.svg" class="w-[48px] h-[48px] mr-[12px]" />
    <div class="bg-slate-50 rounded-lg p-4" :class="{ 'bg-blue-300': isMine }">
      <p>{{ message.body }}</p>
    </div>
  </div>
</template>
