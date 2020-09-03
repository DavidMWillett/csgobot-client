<template>
  <fieldset>
    <legend>Settings</legend>
    <form class="pure-form pure-form-stacked" @submit.prevent="apply">
      <label for="min-price">Minimum Price</label>
      <input v-model.number="settings.minPrice" type="number" id="min-price" class="pure-input-1"/>
      <label for="max-price">Maximum Price</label>
      <input v-model.number="settings.maxPrice" type="number" id="max-price" class="pure-input-1"/>
      <label for="roi1">ROI 1</label>
      <input v-model.number="settings.roi1" type="number" id="roi1" class="pure-input-1"/>
      <label for="roi1-price">ROI 1 Price</label>
      <input v-model.number="settings.roi1Price" type="number" id="roi1-price" class="pure-input-1"/>
      <label for="roi2">ROI 2</label>
      <input v-model.number="settings.roi2" type="number" id="roi2" class="pure-input-1"/>
      <label for="roi2-price">ROI 2 Price</label>
      <input v-model.number="settings.roi2Price" type="number" id="roi2-price" class="pure-input-1"/>
      <label for="blacklist">Blacklist</label>
      <input v-model="settings.blacklist" type="text" id="blacklist" class="pure-input-1"/>
      <button type="submit" class="pure-button pure-button-primary" style="margin-top: 8px; float: right">Apply</button>
    </form>
  </fieldset>
</template>

<script>
const axios = require('axios');

export default {
  name: "SettingsPanel",

  data: function () {
    return {
      settings: {
        minPrice: null,
        maxPrice: null,
        roi1: null,
        roi1Price: null,
        roi2: null,
        roi2Price: null,
        blacklist: ''
      }
    };
  },

  methods: {
    apply: function () {
      axios.post('http://localhost:3000/api/settings', this.settings)
        .then(res => {
          console.log(res);
        })
        .catch(error => {
          console.error(error);
        });
    }
  },

  mounted() {
    axios.get('http://localhost:3000/api/settings').then(response => {
      this.settings = response.data.settings;
    }).catch(error => {
      console.log(error);
    });
  }
}
</script>

<style scoped>

</style>