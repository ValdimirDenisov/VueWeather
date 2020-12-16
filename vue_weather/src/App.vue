<template>
  <div id="app" class="app">
    <div class="informer-container">
      <Temperature v-bind:real_temp="temperatureReal" v-bind:feel_temp="temperatureFeel"/>
      <div class="flex-break"></div>
      <Humidity v-bind:humidity="humidity"/>
      <div class="vertical-divider"></div>
      <Wind v-bind:wind_speed='wind' />

    </div>
  </div>
</template>

<script>
import Temperature from './components/temperature.vue'
import Humidity from './components/humidity.vue'
import Wind from './components/wind.vue'

export default {
  name: 'App',
  data(){
    return {
      temperatureReal: 1,
      temperatureFeel: '-3.2',
      humidity: 6,
      wind: 20
    }
  },
  components: {
    Temperature,
    Humidity,
    Wind
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
