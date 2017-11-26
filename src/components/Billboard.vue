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
  background-image: url('/static/img/black_paper.png');
  color: #FFF;
  height: 100%;
  padding: 10px 30px;
  font-family: Zeynalabdin;
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
