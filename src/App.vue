<template>
  <div>
    <h1>What to Wear Today?</h1>
    <h2 style="color: yellow;">옷 뭐입을지 너무나도 귀찮은데 날씨 보기도 귀찮을때</h2>
    <WeatherFetcher />
  </div>
</template>

<script>
import WeatherFetcher from './components/weather.vue';

export default {
  components: {
    WeatherFetcher,
  },
};
</script>
