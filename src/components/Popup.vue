<template>
<div id="popup">
  <div id="popup-back" class="hide">
    <div id="popup-dark" @click="toggle"></div>
    <div id="popup-content-container">
      <Slider></Slider>
    </div>
  </div>
</div>
</template>

<script>

import Slider from './Slider';

export default {
  name: 'popup',
  data: function() {
    return {
      showed: false
    }
  },
  components: {
    Slider
  },
  methods: {
    toggle: function() {
      this.showed === true? this.hide(): this.show();
    },
    hide: function() {
      document.querySelector('#popup-back').classList.add('hide');
      this.showed = false;
    },
    show: function() {
      document.querySelector('#popup-back').classList.remove('hide');
      this.showed = true;
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

