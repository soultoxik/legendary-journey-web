<template id="board-animal">
<Billboard>
  <p>You exposed <span class="measure">{{measure}} µg/m<sup>3</sup> {{measureName}}</span>  while driving</p>
  <div class="decoration"></div>
  <p> a <span class="animal">{{animal}}</span> will die in <span class="life-exp">{{lifeExp}} hours</span></p>
  <p class="board-resume">Animals are not guilty </p>
  <div v-if="animal === 'dog'" id="animal-dog" class="animal-photo"></div>
  <div v-if="animal === 'cat or dog'" id="animal-cat" class="animal-photo"></div>
  <div v-if="animal === 'chick'" id="animal-chick" class="animal-photo"></div>
  <div v-if="animal === 'goat'" id="animal-goat" class="animal-photo"></div>
  <div v-if="animal === 'hamster'" id="animal-hamster" class="animal-photo"></div>
  <div v-if="animal === 'monkey'" id="animal-monkey" class="animal-photo"></div>
  <div v-if="animal === 'mouse'" id="animal-mouse" class="animal-photo"></div>
  <div v-if="animal === 'pigeon'" id="animal-pigeon" class="animal-photo"></div>
  <div v-if="animal === 'rabbit'" id="animal-rabbit" class="animal-photo"></div>
  <div v-if="animal === 'rat'" id="animal-rat" class="animal-photo"></div>
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

.animal-photo {
  position: absolute;
  top: 75px;
  left: 25px;
  opacity: 0.4;
  width: 300px;
  height: 300px;
  background-size: cover;
}

#animal-cat {
  background-image: url("/static/img/animals/cat.png");
}

#animal-dog {
  background-image: url("/static/img/animals/dog.png");
}

#animal-pigeon {
  background-image: url("/static/img/animals/pigeon.png");
}

#animal-hamster {
  background-image: url("/static/img/animals/hamster.png");
}

#animal-chick {
  background-image: url("/static/img/animals/chick.png");
}

#animal-goat {
  background-image: url("/static/img/animals/goat.png");
}

#animal-monkey {
  background-image: url("/static/img/animals/monkey.png");
}

#animal-mouse {
  background-image: url("/static/img/animals/mouse.png");
}

#animal-rabbit {
  background-image: url("/static/img/animals/rabbit.png");
}

#animal-rat {
  background-image: url("/static/img/animals/rat.png");
}
</style>
