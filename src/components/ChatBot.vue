<template>
  <div>
    <div v-for="(message, index) in messages" :key="index">
      <div :class="{ bot: message.bot }">{{ message.text }}</div>
    </div>
    <input :value="chatInput" @change="sendInput($event)" />
  </div>
</template>

<script>
const url =
  'https://www.cleverbot.com/getreply?key=CC7wpqwalHRc7jRbsB42Pc9-u9A';
export default {
  name: 'HelloWorld',
  data() {
    return {
      chatInput: '',
      messages: [],
    };
  },
  methods: {
    async sendInput(event) {
      const value = event.target.value;
      this.chatInput = value;
      const humanMessage = {
        text: this.chatInput,
        bot: false,
      };
      this.messages.push(humanMessage);
      this.chatInput = '';

      try {
        const response = await fetch(`${url}&input=${this.chatInput}`);
        const data = await response.json();
        const botMessage = {
          text: data.output,
          bot: true,
        };
        this.messages.push(botMessage);
      } catch (error) {
        alert('Error with bot:', error);
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.bot {
  color: red;
}
</style>
