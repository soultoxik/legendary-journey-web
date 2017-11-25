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
  props: [
    'sight'
  ],
  methods: {
    subscript: function(digit) {
      return digit.replace(/(\d+)/g, '<sub>$1</sub>');
    }
  },
  components: {
    Billboard
  }
}
</script>

<style scoped>
</style>
