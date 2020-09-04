<template>
  <ul>
    <li v-for="(message, index) in messages" :key="index" v-bind:class="message.type">
      {{ message.text }}
    </li>
  </ul>
</template>


<script>
const MAX_OUTPUT_LENGTH = 1000;

export default {
  name: "OutputScreen",

  data: function () {
    return {
      messages: []
    };
  },

  methods: {
    addMessage(message) {
      this.messages.push(message);
      if (this.messages.length > MAX_OUTPUT_LENGTH) {
        this.messages.shift();
      }
    }
  },

  sockets: {
    debug(text) {
      this.addMessage({
        type: 'debug',
        text: text
      });
    },
    info(text) {
      this.addMessage({
        type: 'info',
        text: text
      });
    },
    success(text) {
      this.addMessage({
        type: 'success',
        text: text
      });
    },
    errorMsg(text) {
      this.addMessage({
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
  margin: 0 0 0 8px;
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
