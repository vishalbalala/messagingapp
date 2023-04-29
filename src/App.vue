<script setup>
import { ref, onMounted } from 'vue'
import './index.css'
import MessageBox from './components/MessageBox.vue'
import ChatBox from './components/ChatBox.vue'

onMounted(() => {
  getChat()
})
const messages = ref([])

const user = ref({ name: 'vishal' })

const getChat = () => {
  fetch('https://jsonplaceholder.typicode.com/posts')
    .then((response) => response.json())
    .then((json) => (messages.value = json))
}

const addChat = (text) => {
  messages.value.push({
    body: text,
    name: user.value?.name,
    id: messages.value.length
  })
}
</script>

<template>
  <div class="flex justify-center items-center">
    <div class="w-96 relative">
      <div class="mb-16">
        <message-box
          v-for="message in messages"
          :key="message.id"
          :message="message"
          :isMine="user.name === message.name"
        />
      </div>
      <div class="fixed bottom-0 z-90 w-[400px]">
        <chat-box @submit="addChat" />
      </div>
    </div>
  </div>
</template>
