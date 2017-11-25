<template>
<div id="carousel" @click="move">
  <component :is="dynamicComponent" ></component>
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
      if(this.currentSlide === this.slides.length - 1) {
        this.currentSlide = 0;
      } else {
        this.currentSlide++;
      }
    }
  },
  computed: {
    dynamicComponent: function() {
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
