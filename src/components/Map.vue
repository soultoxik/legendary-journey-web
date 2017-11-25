<template>
  <div id="map">
  </div>
</template>

<script>
import {} from 'leaflet';
import config from '../config';

const createMap = () => {
  const map = L.map('map').setView([51.505, -0.09], 13);

  L.tileLayer('https://api.tiles.mapbox.com/v4/{id}/{z}/{x}/{y}.png?access_token={accessToken}', {
    attribution: 'Map data &copy; <a href="http://openstreetmap.org">OpenStreetMap</a> contributors, <a href="http://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, Imagery © <a href="http://mapbox.com">Mapbox</a>',
    maxZoom: 18,
    id: 'mapbox.streets',
    accessToken: config.mapboxToken
  }).addTo(map);
}

export default {
  name: 'map',
  mounted: createMap
}
</script>

<style>
@import url('https://unpkg.com/leaflet@1.2.0/dist/leaflet.css');
#map {
  height: 400px;
}
</style>
