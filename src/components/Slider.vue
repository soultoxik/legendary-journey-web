<template>
<div id="carousel" @click="move">
  <component :is="getSlide" :stationData="stationData"></component>
</div>
</template>

<script>

import BoardAnimal from './BoardAnimal';
import BoardSights from './BoardSights';
import BoardMostPolluted from './BoardMostPolluted';
import BoardParkings from './BoardParkings';

export default {
  name: "slider",
  components: {
    BoardAnimal,
    BoardSights,
    BoardMostPolluted,
    BoardParkings
  },
  props: {
    stationData: {
      required: true
    } 
  },
  data: function() {
    return {
      slides: [
        'board-animal',
        'board-sights',
        'board-most-polluted',
        'board-parkings'
      ],
      currentSlide: 0
    }
  },
  methods: {
    move: function() {
      let show;
      do {
        show = true;

        if(this.currentSlide === this.slides.length - 1) {
          this.currentSlide = 0;
        } else {
          this.currentSlide++;
        }
        
        let name = this.slides[this.currentSlide];
        if(name === 'board-most-polluted' && 
          Number(this.stationData['topPolluted']) === 0) {
            show = false;
          } else {
            if(name === 'board-parkings' && 
              Number(this.stationData['timeToBusStop']) === 0) {
                show = false;
              }
          }
      }
      while(show === false);
    }
  },
  computed: {
    getSlide: function() {
      return this.slides[this.currentSlide];
    }
  }
}
</script>

<style scoped>
#carousel {
  height: 100%;
}
</style>
