<template>
  <div style="margin-top: 16px">
    <fieldset>
      <legend>Controls</legend>
      <div class="pure-g">
        <button v-on:click="start" class="pure-button pure-u-1-2" style="background: green">Start</button>
        <button v-on:click="stop" class="pure-button pure-u-1-2" style="background: red">Stop</button>
      </div>
    </fieldset>
  </div>
</template>

<script>
const axios = require('axios');

function postEmpty(url) {
  axios.post(url, {}, {
    headers: {
      'Content-Type': 'text/plain'
    }
  })
    .then(res => {
      console.log(res);
    })
    .catch(error => {
      console.error(error);
    });
}

export default {
  name: "Control",
  methods: {
    start: function () {
      postEmpty('http://localhost:3000/api/start');
    },
    stop: function () {
      postEmpty('http://localhost:3000/api/stop');
    }
  }
}
</script>

<style scoped>
div {
  display: flex;
}

fieldset {
  flex: auto;
}

button {
  color: white;
  font-size: 125%;
}
</style>