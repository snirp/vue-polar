<template>
  <div id="app">

    <div class="example">
      <polar :angle="0/5*360">🚀</polar>
      <polar :angle="1/5*360">🚌</polar>
      <polar :angle="2/5*360">🚲</polar>
      <polar :angle="3/5*360">🚕</polar>
      <polar :angle="4/5*360">🚤</polar>
    </div>    

    <div class="example">
      <polar
        v-for="n in 8" 
        :key="n"
        :angle="n/5*360"
        :zeroangle="0"
        :setstraight="false"
        :extrarotation="60"
        :width="'100px'"
        :height="'100px'"
        :offset="'120%'"
      >
        <img src="https://cataas.com/cat" width="100%">
      </polar>
    </div>

    <div class="example">
      <!-- The numbers -->
      <polar v-for="n in 12" :key="n" :angle="n/12*360-90" :offset="'150px'" :width="'40px'" :height="'40px'">
        <div class='clock-number'>
          {{n}}
        </div>
      </polar>
      <!-- The hour markers -->
      <polar v-bind="hoursPropsObj" v-for="n in 12" :key="n" :angle="n/12*360"></polar>
      <!-- The minute markers -->
      <polar v-bind="minutesPropsObj" v-for="n in 60" :key="n" :angle="n/60*360"></polar>
      <!-- The hour hand -->
      <polar
        :angle="330"
        :width="'100px'"
        :height="'10px'"
        :offset="'40px'"
        :setstraight="false"
        :customstyles="{
          backgroundColor: 'black',
          borderRadius: '999px'
        }"
      ></polar>
      <!-- The minute hand -->
      <polar 
        :angle="240"
        :width="'120px'"
        :height="'6px'"
        :offset="'50px'"
        :setstraight="false"
        :zindex="99"
        :customstyles="{
          backgroundColor: 'black',
          borderRadius: '999px'
        }"
      ></polar>
    </div>

    <div class="example">
      <polar
        v-for="n in 60" 
        :key="n" 
        :angle="n/-30.3*360"
        :offset="n*3+'px'"
        :zindex="n"
        :width="(2+n/2)+'px'"
        :height="(2+n/2)+'px'"
        :customstyles="{
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
    this.hoursPropsObj = {
      width: '20px',
      height: '5px',
      offset: '110px',
      setstraight: false,
      zindex: 2,
      customstyles: {
        backgroundColor: 'red'
      }
    };
    this.minutesPropsObj = {
      width: '10px',
      height: '3px',
      offset: '115px',
      setstraight: false,
      zindex: 1,
      customstyles: {
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
