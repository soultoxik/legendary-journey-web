<template id="board-parkings">
<Billboard>
  <p>Ближайшая остановка общественного транспорта в
    <span class="time-to-bus-stop">{{timeToBusStop}}</span>
    минутах ходьбы отсюда.</p>
  <p class="board-resume">Общественный транспорт решает</p>
</Billboard>
</template>

<script>

import Billboard from "./Billboard";

export default {
  name: 'board-parkings',
  props: [
    'timeToBusStop'
  ],
  components: {
    Billboard
  }
}
</script>

<style scoped>
</style>
