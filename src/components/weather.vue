<template>
  <div class="weather-fetcher">
    <h2>날씨 검색</h2>
    <input v-model="city" placeholder="도시 이름 입력 (예: Seoul)" />
    <button @click="fetchWeather">날씨 확인</button>

    <div v-if="weather">
      <p><strong>도시:</strong> {{ weather.name }}</p>
      <p><strong>기온:</strong> {{ weather.main.temp }}°C</p>
      <p><strong>날씨:</strong> {{ weather.weather[0].main }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      city: '',
      weather: null,
    };
  },
  methods: {
    async fetchWeather() {
      const apiKey = import.meta.env.VITE_WEATHER_API_KEY;
      console.log("API KEY:", apiKey);
      const url = `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${apiKey}&units=metric`;

      try {
        const res = await fetch(url);
        if (!res.ok) throw new Error('도시를 찾을 수 없습니다.');
        const data = await res.json();
        this.weather = data;
      } catch (err) {
        alert(err.message);
        this.weather = null;
      }
    },
  },
};
</script>

<style scoped>
.weather-fetcher {
  padding: 1rem;
  max-width: 400px;
  margin: auto;
  text-align: center;
}
input {
  padding: 0.5rem;
  margin-right: 0.5rem;
}
button {
  padding: 0.5rem 1rem;
}
</style>
