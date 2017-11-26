<template id="board-animal">
<Billboard>
  <p>You exposed <span class="measure">{{measure}} µg/m<sup>3</sup> {{measureName}}</span>  while driving</p>
  <div class="decoration"></div>
  <p> a <span class="animal">{{animal}}</span> will die in <span class="life-exp">{{lifeExp}} hours</span></p>
  <p class="board-resume">Animals are not guilty </p>
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
    let animals = this.stationData['animals'];
    let animal = animals[Math.floor(Math.random()*animals.length)];
    let infos = animal['info'];
    let info = infos[Math.floor(Math.random()*infos.length)];

    let pretty = function(duration) {
        var milliseconds = parseInt((duration%1000)/100)
            , seconds = parseInt((duration/1000)%60)
            , minutes = parseInt((duration/(1000*60))%60)
            , hours = parseInt((duration/(1000*60*60))%24);

        hours = (hours < 10) ? "0" + hours : hours;
        minutes = (minutes < 10) ? "0" + minutes : minutes;
        seconds = (seconds < 10) ? "0" + seconds : seconds;
        if(hours === 0) return minutes;
        return hours;
    }

    return {
      measure: info['concentration'],
      measureName: info['measure'],
      animal: animal['animal'],
      lifeExp: pretty(info['lifeexp'])
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
