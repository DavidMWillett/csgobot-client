<template>
  <div id="app">
    <ControlPanel/>
    <OutputScreen/>
  </div>
</template>

<script>
import ControlPanel from '@/components/ControlPanel';
import OutputScreen from '@/components/OutputScreen';

export default {
  name: 'App',
  components: {
    ControlPanel,
    OutputScreen
  },
  sockets: {
    connect: function () {
      console.log("Socket connected.")
    },
    getCode: function (fn) {
      const code = prompt("Enter Steam Guard code");
      fn(code);
    }
  }
}
</script>

<style>
html, body {
  height: 100%;
  margin: 0;
}

#app {
  display: flex;
  flex-direction: column;
  box-sizing: border-box;
  height: 100%;
  padding: 8px;
}
</style>
