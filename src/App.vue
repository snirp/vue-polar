<template>
  <div id="app">

    <div class="example">
      <polar :item="0" :segments="5">🚀</polar>
      <polar :item="1" :segments="5">🚌</polar>
      <polar :item="2" :segments="5">🚲</polar>
      <polar :item="3" :segments="5">🚕</polar>
      <polar :item="4" :segments="5">🚤</polar>
    </div>    

    <div class="example">
      <polar 
        v-for="n in 8" 
        :key="n" 
        :item="n" 
        :segments="5"
        :zeroAngle="0"
        :setStraight="false"
        :extraRotation="60"
        :width="'100px'"
        :height="'100px'"
        :offset="'120%'"
      >
        <img src="https://cataas.com/cat" width="100%">
      </polar>
    </div>

    <div class="example">
      <!-- The hour numbers -->
      <polar v-bind="numbersPropsObj" v-for="n in 12" :key="n" :item="n">
        <div class='clock-number'>
          {{n}}
        </div>
      </polar>
      <!-- The hour markers -->
      <polar v-bind="hoursPropsObj" v-for="n in 12" :key="n" :item="n" />
      <!-- The minute markers -->
      <polar v-bind="minutesPropsObj" v-for="n in 60" :key="n" :item="n" />
      <!-- The hour hand -->
      <polar 
        :item="9"
        :segments="60" 
        :width="'100px'"
        :height="'10px'"
        :offset="'40px'"
        :zeroAngle="270"
        :setStraight="false"
        :customStyles="{
          backgroundColor: 'black',
          borderRadius: '999px'
        }"
      />
      <!-- The minute hand -->
      <polar 
        :item="51"
        :segments="60" 
        :width="'120px'"
        :height="'6px'"
        :offset="'50px'"
        :zeroAngle="270"
        :setStraight="false"
        :zIndex="99"
        :customStyles="{
          backgroundColor: 'black',
          borderRadius: '999px'
        }"
      />
    </div>

    <div class="example">
      <polar
        v-for="n in 60" 
        :key="n" 
        :item="n"
        :segments="-30.3" 
        :offset="n*3+'px'"
        :zIndex="n"
        :width="(2+n/2)+'px'"
        :height="(2+n/2)+'px'"
        :customStyles="{
          borderRadius: '50%',
          backgroundColor: '#'+('000000'+Math.floor(0xFFFFFF*(n/60)).toString(16)).slice(-6),
        }"
      />
    </div>

  </div>
</template>

<script>
import Polar from './components/Polar.vue'

export default {
  created(){
    this.numbersPropsObj = {
      segments: 12,
      zeroAngle: 270,
      offset: '150px',
      width: '40px',
      height: '40px'
    };
    this.hoursPropsObj = {
      segments: 12,
      width: '20px',
      height: '5px',
      offset: '110px',
      setStraight: false,
      zIndex: 2,
      customStyles: {
        backgroundColor: 'red'
      }
    };
    this.minutesPropsObj = {
      segments: 60,
      width: '10px',
      height: '3px',
      offset: '115px',
      setStraight: false,
      zIndex: 1,
      customStyles: {
        backgroundColor: 'grey'
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
.example{
  position: relative;
  width: 400px;
  height: 400px;
  font-size: 2.5rem;
}
.clock-number{
  width: 100%;
  height: 100%;
  background-color: black;
  color: white;
  font-size: 1.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
}
</style>
