<template id="billboard">
<div class="board">
  <div class="container">
    <slot></slot>
  </div>
</div>
</template>

<script>

export default {
  name: 'billboard'
}
</script>

<style scoped>
.board {
  background-color: #000;
  color: #FFF;
  height: 100%;
}
.board * {
  margin: auto;
  text-align: center;
}
.board p {
  margin: 20px 0px;
  font-size: 5vw;
}
.board span {
  font-weight: bold;
  font-size: 6vw;
}

</style>
