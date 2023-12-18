<template>
  <div id="app">
    <div class="img-container">
      <img 
           @mousemove="onMouseMoving"
           @mouseout="onMouseOut"
           @mouseenter="onMouseEnter"
           class="img" 
           src="./assets/violao.jpg" 
           alt="Violão">           
      <TooltipCard :coordinates="coordinates" v-if="isInside">Vamos estudar mais!!</TooltipCard>
    </div>
  </div>
</template>

<script>

import TooltipCard from './components/TooltipCard.vue';

export default {
  name: 'App',
  components: {
    TooltipCard    
  },

  data() {
    return {
      isInside: false,
      coordinates: {
        left: 0,
        top: 0
      }
    }
  },

  methods: {
    onMouseEnter() {
      this.isInside = true;
    },

    onMouseOut() {
      this.isInside = false;
    },

    onMouseMoving( event ) {
      const { offsetX, offsetY } = event;
      this.coordinates.left = offsetX + 'px';
      this.coordinates.top = offsetY + 'px';
    }
  }
}
</script>

<style>
  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  html {
    height: 100vh;
    font-family: Arial, Helvetica, sans-serif;
  }

  body {
    background-color: #253237;
  }

  #app {
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .img-container {
    position: relative;
  }

  .img {
    border-radius: 5px;
    box-shadow: 0px 0px 0px 5px rgba(255, 255, 255, .5) ;
  }
</style>
