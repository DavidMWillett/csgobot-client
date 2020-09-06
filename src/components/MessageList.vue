<template>
  <ul>
    <MessageItem
      v-for="message in messages"
      v-bind:message="message"
      v-bind:key="message.id"
    />
  </ul>
</template>


<script>
import MessageItem from "@/components/MessageItem";

const MAX_OUTPUT_LENGTH = 1000;
let messageId = 0;

export default {
  name: "MessageList",

  components: {
    MessageItem
  },

  data: function () {
    return {
      messages: []
    };
  },

  methods: {
    addMessage(message) {
      message.id = messageId++;
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
        type: 'error',
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

ul {
  flex-grow: 1;
  margin: 0 0 0 8px;
  border: 1px solid #000;
  overflow: auto;
  padding: 8px;
  list-style: none;
  background-color: #1d3030;
}
</style>
