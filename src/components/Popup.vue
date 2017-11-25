<template>
<div id="popup">
  <div id="popup-back" class="hide" @click="toggle">
    <div id="popup-content-container">
      <slot></slot>
    </div>
  </div>
</div>
</template>

<script>
import $ from "jquery";

export default {
  name: 'popup',
  data: function() {
    return {
      showed: false
    }
  },
  methods: {
    toggle: function() {
      this.showed === true? this.hide(): this.show();
    },
    hide: function() {
      $('#popup-back').addClass('hide');
      this.showed = false;
    },
    show: function() {
      $('#popup-back').removeClass('hide');
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
  background-color: rgba(0, 0, 0, 0.5);
  overflow: hidden;
}

#popup-content-container {
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

