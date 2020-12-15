<template>
    <div class="temperature">
        <img src="img/thermometer.png">
        <div class="temp-real">{{real_temp}}</div>
        <div class="temp-feel">{{feel_temp}}</div>
      </div>
</template>

<script>
export default {
  name: 'Temperature',
  props: ['real_temp', 'feel_temp']
}
</script>