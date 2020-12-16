<template>
    <div class="wind" v-on:click="reload_data()">
        <img src="img/wind.png"> {{wind_speed}} <small>м/с</small>
    </div>
</template>

<script>
export default {
  name: 'Wind',
  props: ['wind_speed'],
  methods: {
     reload_data() {
      alert(wind_speed);
      let xhr = new XMLHttpRequest;
      xhr.open('GET', 'http://37.77.104.246/api/weather/wind.php', true);
      xhr.send();
      xhr.addEventListener('readystatechange', function() {
        if (xhr.readyState == 4 && xhr.status == 200) {
          this.wind_speed = xhr.responseText;
        } else {
          this.wind_speed = 0;
        }
      });
    }
  }
}
</script>