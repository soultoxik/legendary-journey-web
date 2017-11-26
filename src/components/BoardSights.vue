<template id="board-sights">
<Billboard>
  <p>А если бы вы ехали общественным транспортом,
    смогли бы увидеть <span class="sight">{{sight}}</span></p>
  <p class="board-resume">Общественный транспорт решает</p>
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
