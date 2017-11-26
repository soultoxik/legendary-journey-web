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
import config from './config';

export default {
  name: 'app',
  components: {
    'BillboardMap': Map,
    Popup
  },
  methods: {
    getData: function(coords) {
      return new Promise((resolve, reject) => {
        fetch(`${config.dataServer}/fullinfo/${coords[0]}/${coords[1]}`)
          .then((response) => {
            if(response.ok) {
              resolve(response.json());
            } else {
              throw 'Network error';
            }
          });
      });
    },
    openPopup: function(coords) {
      this.getData(coords)
        .then((json) => {
          this.$refs.child.show(json);
        });
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
