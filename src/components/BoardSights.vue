<template id="board-sights">
<Billboard>
  <p>You will never see <span class="sight">{{sight}}</span>
    while driving</p>
    <p> Want to seat, relax and enjoy the view?
  </p>
  <p class="board-resume">Use public transport</p>
</Billboard>
</template>

<script>

import Billboard from "./Billboard";

export default {
  name: 'board-sights',
  props: {
    stationData: {
      required: true
    }
  },
  methods: {
    subscript: function(digit) {
      return digit.replace(/(\d+)/g, '<sub>$1</sub>');
    }
  },
  data: function() {
    let sights = this.stationData['sights'];
    let sight = sights[Math.floor(Math.random()*sights.length)];
    return {
      sight: sight
    }
  },
  components: {
    Billboard
  }
}
</script>

<style scoped>
</style>
