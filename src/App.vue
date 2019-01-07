<template>
  <div id="app">
    <div class="test">
      Test with referenced prop object + nested styles object
      <polar v-bind="propObj" v-for="n in 12" :key="n" :item="n">{{n}}</polar>
    </div>
    <hr/>
    <div class="test">
      Test with inline prop object + nested styles object
      <polar v-bind="{segments:12,customStyles:{borderRadius:'50%', backgroundColor:'pink'}}" v-for="n in 12" :key="n" :item="n">{{n}}</polar>
    </div>
    <hr/>
    <div class="test">
      Test with referenced prop object, no styles object
      <polar v-bind="propObjNoNested" v-for="n in 12" :key="n" :item="n">{{n}}</polar>
    </div>
  </div>
</template>

<script>
import Polar from './components/Polar.vue'

export default {
  data(){
    return {
      propObj: {
        segments: 12,
        customStyles: {
          borderRadius: '50%',
          backgroundColor: 'pink'
        }
      },
      propObjNoNested: {
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
.test{
  position: relative;
  width: 400px;
  height: 200px;
}

</style>
