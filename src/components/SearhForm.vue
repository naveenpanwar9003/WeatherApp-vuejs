<template>
  <form @submit.prevent="getWeather()" class="flex justify-center">
    <input
      type="text"
      placeholder="Search City/Country Name"
      v-model="searchTerm"
      class="mr-4 flex-1 px-4 py-2 rounded"
    />
    <button class="py-2 px-6 rounded bg-blue-700 font-bold text-white">
      Search
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      searchTerm: "",
      weatherResult: {},
    };
  },

  methods: {
    async getWeather() {
      try {
        const res = await fetch(
          `https://api.openweathermap.org/data/2.5/weather?q=${this.searchTerm}&APPID=ff9ee543810318a7b86c44f55044b656&units=metric`
        );
        const data = await res.json();
        const resultData = {
          temp: data.main.temp,
          name: data.name,
          humidity: data.main.humidity,
          pressure: data.main.pressure,
        };

        this.weatherResult = resultData;

        this.$emit("weatherRecieved", this.weatherResult);
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>