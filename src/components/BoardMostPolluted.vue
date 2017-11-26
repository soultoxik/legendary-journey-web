<template id="board-most-polluted">
<Billboard>
  <p> You're approaching one of the most polluted areas! </p>
    <p> Do you care?</p>
  <p class="board-resume">What about using a tram instead?</p>
</Billboard>
</template>

<script>

import Billboard from "./Billboard";

export default {
  name: 'board-most-polluted',
  components: {
    Billboard
  }
}
</script>

<style scoped>
</style>
