<template id="board-parkings">
<Billboard>
  <p>Nearest bus stop is only a
    <span class="time-to-bus-stop">{{timeToBusStop}}</span>
    minutes walk from here.</p>
  <p class="board-resume">It's faster!</p>
</Billboard>
</template>

<script>

import Billboard from "./Billboard";

export default {
  name: 'board-parkings',
  props: {
    stationData: {
      required: true
    }
  },
  data: function() {
    return {
      timeToBusStop: this.stationData['timeToBusStop']
    }
  },
  components: {
    Billboard
  }
}
</script>

<style scoped>
</style>
