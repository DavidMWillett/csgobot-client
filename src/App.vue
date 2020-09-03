<template>
  <div id="app" class="pure-g">
    <div class="pure-u-1-5">
      <SettingsPanel />
      <ControlPanel />
    </div>
    <div class="pure-u-4-5" style="height: 100%; display: flex">
      <OutputScreen />
    </div>
  </div>
</template>

<script>
import ControlPanel from '@/components/ControlPanel';
import SettingsPanel from '@/components/SettingsPanel';
import OutputScreen from '@/components/OutputScreen';

export default {
  name: 'App',
  components: {
    ControlPanel,
    SettingsPanel,
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
}

#app {
  box-sizing: border-box;
  height: 100%;
  padding: 8px;
}
</style>
