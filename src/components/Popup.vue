<template>
<div id="popup">
  <div id="popup-back" class="hide">
    <div id="popup-dark" @click="hide"></div>
    <div id="popup-content-container">
      <Slider v-if="showed" :stationData="stationData"></Slider>
    </div>
  </div>
</div>
</template>

<script>

import Slider from './Slider';
import config from '../config';

export default {
  name: 'popup',
  data: function() {
    return {
      showed: false,
      stationData: {},
      coords: {}
    }
  },
  components: {
    Slider
  },
  methods: {
    hide: function() {
      document.querySelector('#popup-back').classList.add('hide');
      this.showed = false;
    },
    show: function(coords) {
      this.coords = coords;

      this.loadData()
        .then((data) => {
          this.stationData = data;
          document.querySelector('#popup-back').classList.remove('hide');
          this.showed = true;
        })

      setInterval(function () {
        if(this.showed) {
          this.loadData()
            .then((data) => {
              this.stationData = data;
            })
        }
      }.bind(this), 5000); 
    },
    loadData: function() {
      return new Promise((resolve, reject) => {
        fetch(`${config.dataServer}/fullinfo/${this.coords.lat}/${this.coords.lng}`)
          .then((response) => {
            if(response.ok) {
              resolve(response.json());
            } else {
              throw 'Network error';
            }
          });
      });
    }
  }
}
</script>

<style scoped>
#popup-back {
  position: absolute;
  top: 0px;
  left: 0px;
  right: 0px;
  bottom: 0px;
  overflow: hidden;
}

#popup-dark {
  position: absolute;
  top: 0px;
  left: 0px;
  right: 0px;
  bottom: 0px;
  background-color: rgba(0, 0, 0, 0.5);
}

#popup-content-container {
  position: relative;
  width: 90%;
  height: 90%;
  background-color: #FFFFFF;
  margin: auto;
  margin-top: 5vh;
  border-radius: 25px;
}

.hide {
  width: 0px;
  height: 0px;
}
</style>

