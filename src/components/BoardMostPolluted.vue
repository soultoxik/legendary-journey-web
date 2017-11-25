<template id="board-most-polluted">
<Billboard>
  <p>Вы приближаетесь к самой загрезняемой точке!
    Возможно, пора искать обходной путь?</p>
  <p class="board-resume">Общественный транспорт решает</p>
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
