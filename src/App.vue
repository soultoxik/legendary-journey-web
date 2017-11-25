<template>
  <div id="app">
    <Map v-on:popup="openPopup"></Map>
    <Popup ref="child">
      test
    </Popup>
  </div>
</template>

<script>
import Map from './components/Map';
import Popup from './components/Popup';

export default {
  name: 'app',
  components: {
    Map,
    Popup
  },
  methods: {
    openPopup: function() {
      this.$refs.child.toggle();
    }
  }
}
</script>

<style>
html, body {
  height: 100%;
  overflow-y: hidden;
  overflow-x: hidden;
  margin: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
