<template>
  <div>
    <button v-on:click="start">Start</button>
    <button v-on:click="stop">Stop</button>
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

</style>