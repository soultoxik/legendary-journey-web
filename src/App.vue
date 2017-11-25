<template>
  <div id="app">
    <Map></Map>
  </div>
</template>

<script>
import Map from './components/Map'

export default {
  name: 'app',
  components: {
    Map
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
