<template>
  <div id="app">
    <div class="plant">
      <img class="plant-holo" src="./assets/holo.png">
      <img class="plant-mineral" v-bind:src="plantimg">
      <img class="plant-miner-1" src="./assets/work.gif">
      <img class="plant-miner-2" src="./assets/work.gif">
      <img class="plant-miner-3" src="./assets/work.gif">
      <img class="plant-miner-4" src="./assets/work.gif">
      <img class="plant-miner-5" src="./assets/work.gif">
      <img class="plant-miner-6" src="./assets/work.gif">
    </div>
    <!-- <HelloWorld/> -->
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import plant100 from './assets/plant.png'
import plant50 from './assets/50.png'
import plant25 from './assets/25.png'
import plant0 from './assets/0.png'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data () {
    return {
      count: 0,
      plantimg: plant100,
      plantArr: [plant100, plant50, plant25, plant0]
    }
  },
  created () {
    // this.inter = setInterval(() => {
    //   this.count >= 3 ? this.count = 0 : this.count++
    //   this.plantimg = this.plantArr[this.count]
    // }, 5000)
  },
  destroyed () {
    clearInterval(this.inter)
  }
}
</script>
<style lang="scss">
@import 'reset';

$planttime: 100s;
$updowntime: 4s;

@mixin plantMiner($top, $left) {
  width: 1rem;
  height: 1rem;
  top: $top;
  left: $left;
}

#app {
  width: 100vw;
  height: 100vh;
  background: url(./assets/pbg.png);
  background-size: 100% 100%;
  text-align: center;
  white-space: nowrap;
  overflow: hidden;
  & .plant {
    position: relative;
    animation: move $updowntime linear infinite;
    top: 1.39rem;
    & img {
      position: absolute;
    }
    & .plant-holo {
      width: 3.62rem;
      height: 3.62rem;
      left: 0.06rem;
      animation: loading 80s linear infinite;
    }
    & .plant-mineral {
      width: 2.8rem;
      height: 2.8rem;
      left: 0.47rem;
      top: 0.40rem;
      animation: loadingreverse $planttime linear infinite;
      // animation: fadeout 2s linear;
    }
    & .plant-miner-1 {
      @include plantMiner(-0.3rem, 50%);
      margin-left: -0.65rem;
    }
    & .plant-miner-2 {
      @include plantMiner(0.2rem, 0rem);
      transform: rotate(-60deg);
    }
    & .plant-miner-3 {
      @include plantMiner(1.6rem, 0rem);
      transform: rotate(-120deg);
    }
    & .plant-miner-4 {
      @include plantMiner(2.8rem, 1.25rem);
      transform: rotate(-180deg);
    }
    & .plant-miner-5 {
      @include plantMiner(1.6rem, 2.8rem);
      transform: rotate(120deg);
    }
    & .plant-miner-6 {
      @include plantMiner(0.2rem, 2.8rem);
      transform: rotate(60deg);
    }
  }
}
@keyframes loading {
  0% {
    transform: rotate(0);
  }
  100% {
    transform: rotate(360deg);
  }
}
@keyframes loadingreverse {
  0% {
    transform: rotate(360deg);
  }
  100% {
    transform: rotate(0);
  }
}
@keyframes move {
  0% {
    transform: translateY(0);
  }
  25% {
    transform: translateY(5px);
  }
  50% {
    transform: translateY(10px);
  }
  75% {
    transform: translateY(5px);
  }
  100% {
    transform: translateY(0);
  }
}
@keyframes fadeout {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
