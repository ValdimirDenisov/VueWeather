<template>
    <div class="wind">
        <img src="img/wind.png"> {{wind_speed}} <small>м/с</small>
    </div>
</template>

<script>
export default {
  name: 'Wind',
  props: ['wind_speed'],
}
</script>