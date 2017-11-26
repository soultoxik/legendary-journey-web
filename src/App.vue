<template>
  <div id="app">
    <BillboardMap v-on:popup="openPopup"></BillboardMap>
    <Popup ref="child">

    </Popup>
  </div>
</template>

<script>
import Map from './components/Map';
import Popup from './components/Popup';

export default {
  name: 'app',
  components: {
    'BillboardMap': Map,
    Popup
  },
  methods: {
    openPopup: function(coords) {
      this.$refs.child.show(coords);
    }
  }
}
</script>

<style>
@font-face { 
  font-family: Zeynalabdin; 
  src: url('/static/fonts/Zeynalabdin.otf');
}

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
