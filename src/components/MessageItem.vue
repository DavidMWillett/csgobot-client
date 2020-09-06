<template>
  <li v-bind:class="message.type">{{ message.text }}</li>
</template>


<script>
export default {
  name: "MessageItem",
  props: ['message']
}
</script>


<style scoped>
@import url('https://fonts.googleapis.com/css?family=Roboto+Mono');

li {
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

li.error {
  color: red;
}
</style>