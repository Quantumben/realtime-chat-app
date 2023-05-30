<template>
    <div class="chat-container">
      <div class="messages">
        <div v-for="message in messages" :key="message.id" class="message">
          <strong>{{ message.user }}</strong>: {{ message.content }}
        </div>
      </div>
      <div class="input-area">
        <input v-model="newMessage" @keyup.enter="sendMessage" type="text" placeholder="Type your message here...">
      </div>
    </div>
  </template>

  <script>
  export default {
    data() {
      return {
        messages: [],
        newMessage: '',
      };
    },
    methods: {
      sendMessage() {
        // Logic to send a new message will go here
      },
    },
  };
  </script>
