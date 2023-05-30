<template>
    <div class="chat-container">
        <div class="messages">
            <div v-for="message in messages" :key="message.id" class="message">
                <strong>{{ message.user }}</strong
                >: {{ message.content }}
            </div>
        </div>
        <div class="input-area">
            <input
                v-model="newMessage"
                @keyup.enter="sendMessage"
                type="text"
                placeholder="Type your message here..."
            />
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            messages: [],
            newMessage: "",
        };
    },
    methods: {
        async sendMessage() {
            if (this.newMessage.trim() === "") return;

            const response = await axios.post("/send-message", {
                content: this.newMessage,
            });
            this.messages.push(response.data);
            this.newMessage = "";
            this.socket.emit("send-message", response.data);
        },
    },
};
</script>
