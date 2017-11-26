<template id="board-animal">
<Billboard>
  <p>Вы выделили <span class="measure">{{measure}} µg/m<sup>3</sup> {{measureName}}</span></p>
  <div class="decoration"></div>
  <p><span class="animal">{{animal}}</span>, дышащий таким воздухом,
    умрет через <span class="life-exp">{{lifeExp}} дней</span></p>
  <p class="board-resume">Общественный транспорт решает</p>
</Billboard>
</template>

<script>

import Billboard from './Billboard';

export default {
  name: 'board-animal',
  props: {
    stationData: {
      required: true
    }
  },
  data: function() {
    console.log(this.stationData);
    let animals = this.stationData['animals'];
    let animal = animals[Math.floor(Math.random()*animals.length)];
    let infos = animal['info'];
    let info = infos[Math.floor(Math.random()*infos.length)];

    return {
      measure: info['concentration'],
      measureName: info['measure'],
      animal: animal['animal'],
      lifeExp: info['lifeexp']
    }
  },
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

.decoration {
  width: 50px;
  height: 60px;

  background-image: url("/static/img/approximatelyEqualTo.png");
  background-size: cover;
}

</style>
