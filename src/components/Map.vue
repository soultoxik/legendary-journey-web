<template>
  <div id="map">
  </div>
</template>

<script>
import L from 'leaflet';
import config from '../config';


// hack to use leaflet with webpack
// https://github.com/PaulLeCam/react-leaflet/issues/255#issuecomment-269750542
delete L.Icon.Default.prototype._getIconUrl;
L.Icon.Default.mergeOptions({
  iconRetinaUrl: require('leaflet/dist/images/marker-icon-2x.png'),
  iconUrl: require('leaflet/dist/images/marker-icon.png'),
  shadowUrl: require('leaflet/dist/images/marker-shadow.png'),
});

export default {
  name: 'map',
  mounted: function() {
    this.renderMap();
  },
  data: function() {
    return {
      map: undefined,
      featureGroup: undefined
    }
  },
  methods: {
    openPopup: function() {
      this.$emit('popup');
    },
    createMap: function() {
      this.map = L.map('map').setView(config.map.center, config.map.zoom);

      L.tileLayer('https://api.tiles.mapbox.com/v4/{id}/{z}/{x}/{y}.png?access_token={accessToken}', {
        attribution: 'Map data &copy; <a href="http://openstreetmap.org">OpenStreetMap</a> contributors, <a href="http://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, Imagery © <a href="http://mapbox.com">Mapbox</a>',
        maxZoom: 18,
        id: 'mapbox.streets',
        accessToken: config.map.mapboxToken
      }).addTo(this.map);

      this.featureGroup = L.featureGroup().addTo(this.map).on("click", this.openPopup);
    },
    getCoordinates: function() {
      return new Promise((resolve, reject) => {
        let trackedCoordinates = [];

        fetch(config.dataServer)
          .then((response) => {
            if(response.ok) {
              return response.json();
            }
        
            throw 'Network error';
          })
          .then((json) => {
            json['stations'].forEach((station) => {
              trackedCoordinates.push(station['coord']);
            });
          })
          .then(() => {
            resolve(trackedCoordinates);
          });
      });
    },
    renderMap: function() {
      this.createMap();

      this.getCoordinates()
        .then((coordinates) => {
          coordinates.forEach((coordinate) => {
            L.marker(coordinate).addTo(this.featureGroup);
          });
        });
    }
  }
}
</script>

<style scoped>
@import url('~leaflet/dist/leaflet.css');
#map {
  height: 100vh;
  width: 100vw;
  z-index: 0;
}
</style>
