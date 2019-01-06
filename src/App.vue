<template>
  <div id="app">
    <polar v-bind="numbersPropObj" v-for="n in 12" :key="n" :item="n">{{n}}</polar>
  </div>
</template>

<script>
import Polar from './components/Polar.vue'

export default {
  data(){
    return {
      numbersPropObj: {
        zeroAngle: 270,
        segments: 12,
      }
    }
  },
  name: 'app',
  components: {
    Polar
  }
}
</script>

<style>
#app{
  position: relative;
  width: 200px;
  height: 200px;
}

</style>
