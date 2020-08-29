<template>
  <ul>
    <li v-for="(message, index) in messages" :key="index" v-bind:class="message.type">
      {{ message.text }}
    </li>
  </ul>
</template>

<script>
export default {
  name: "OutputScreen",

  data: function () {
    return {
      messages: []
    };
  },

  sockets: {
    debug(text) {
      this.messages.push({
        type: 'debug',
        text: text
      });
    },
    info(text) {
      this.messages.push({
        type: 'info',
        text: text
      });
    },
    success(text) {
      this.messages.push({
        type: 'success',
        text: text
      });
    },
    errorMsg(text) {
      this.messages.push({
        type: 'error-msg',
        text: text
      });
    },
  },

  updated: function () {
    const elem = this.$el;
    elem.scrollTop = elem.scrollHeight;
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Roboto+Mono');

ul {
  flex-grow: 1;
  margin-top: 8px;
  margin-bottom: 0;
  border: 1px solid #000;
  overflow: auto;
  padding: 8px;
  list-style: none;
  background-color: #1d3030;
  font-family: 'Roboto Mono', monospace;
  font-size: 14px;
}

li.debug {
  color: gray;
}

li.info {
  color: white;
}

li.success {
  color: green;
}

li.error-msg {
  color: red;
}
</style>
