<template>
    <div class="humidity">
        <img src="img/humidity.png"> {{humidity}} <small>%</small>
    </div>
</template>

<script>
export default {
  name: 'Humidity',
  props: ['humidity'],
}
</script>