<template>
  <ChatBot />
</template>

<script>
import ChatBot from './components/ChatBot.vue';
export default {
  name: 'App',
  components: {
    ChatBot,
  },
};
</script>

<style>
html,
body {
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
