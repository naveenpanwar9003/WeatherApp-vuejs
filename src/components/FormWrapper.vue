<template>
  <div class="bg-white bg-opacity-50 p-8 rounded">
    <SearchForm @weatherRecieved="showWeather" />
    <div class="flex flex-wrap -mx-2 mt-4" v-if="weatherResult">
      <Card card-name="Temperature" :card-value="weatherResult.temp" />
      <Card card-name="Name" :card-value="weatherResult.name" />
      <Card card-name="Pressure" :card-value="weatherResult.pressure" />
      <Card card-name="Humidty" :card-value="weatherResult.humidity" />
    </div>
  </div>
</template>

<script>
import SearchForm from "./SearhForm.vue";
import Card from "./Card.vue";

export default {
  data() {
    return {
      weatherResult: "",
    };
  },
  components: {
    SearchForm,
    Card,
  },

  methods: {
    showWeather(value) {
      this.weatherResult = { ...value };
    },
  },
};
</script>