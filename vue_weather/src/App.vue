<template>
  <div id="app" class="app">
    <div class="informer-container">
      <Temperature v-bind:real_temp="temperatureReal" v-bind:feel_temp="temperatureFeel"/>
      <div class="flex-break"></div>
      <Humidity v-bind:humidity="humidity"/>
      <div class="vertical-divider"></div>
      <Wind v-bind:wind_speed='wind'/>
      {{getWeather()}}
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
  },
  methods: {
    getWeather() {
      let api_w = {
        coordinates: '56.011759, 37.859407',
        a_id: '082dcc0a',
        a_key: '0e1fd3c764d42e908f2ccfacbbeca952'
      }
      let url = 'http://api.weatherunlocked.com/api/current/'+ api_w['coordinates'] + '?app_id=' + api_w['a_id'] + '&app_key=' + api_w['a_key'];
      this.axios.get(url)
        .then((response) => {
          let arr = response['data'];
          this.wind = arr['windspd_ms'];
          this.temperatureReal = arr['temp_c'];
          this.temperatureFeel = arr['feelslike_c'];
          this.humidity = arr['humid_pct'];
        });
    }
  },
  mounted() {
    setInterval(this.getWeather(), 10000);
  }
}
</script>

<style>
  body {
    margin: 0;
    padding: 0;
  }
  .app {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    background: rgb(244, 123, 186);
    background: linear-gradient(-25deg, rgba(244, 123, 186, 0.5) 20%, rgba(90, 95, 245, 0.5) 80%);
  }
  .informer-container {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    flex-wrap: wrap;
    width: 400px;
    padding: 30px;
    background-image: url('assets/img/forest.png');
    background-size: cover;
    background-position: center center;
    border-radius: 20px;
    box-shadow: 0px 0px 10px 0px rgba(50, 50, 50, 0.75);
  }
  
  .flex-break{
    flex-basis: 100%;
    height: 0;
  }
  .vertical-divider{
    height: 70px;
    width: 1px;
    background-color: #fff;
    vertical-align: middle;
    display: table-cell;
  }
</style>
