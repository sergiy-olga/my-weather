<template>
  <div class="v-input">
    <input type="text" v-model="city" />
    <ul class="input-list" v-show="isOpen">
      <li
        v-for="(cityValue, index) in info"
        :key="index"
        placeholder="Введіть назву насеного пункту"
        v-on:click="selectCity(cityValue)"
        @keyup.enter="selectCity"
      >
        {{ cityValue.name }}, {{ cityValue.state }}
      </li>
    </ul>
    <p>{{ test }}</p>
    <div v-show="isOpenInfo">
      <v-info-weather :weatherInfo="inf"></v-info-weather>
    </div>
    <!-- <p>{{ inf }}</p> -->
  </div>
</template>

<script>
import { ref, watch } from "vue";
import axios from "axios";
import vInfoWeather from "./v-infoWeather.vue";
export default {
  components: { vInfoWeather },
  name: "v-input",
  props: {},
  setup() {
    const apiKey = ref("22c43bb03023776cb8d7f02862a80c7c");
    const baseUrl = ref("http://api.openweathermap.org/geo/1.0/direct");
    const cityName = ref("");
    const city = ref("");
    const info = ref("");
    const lat = ref("");
    const lon = ref("");
    const inf = ref([]);
    const isOpen = ref(false);
    const test = ref("");
    const isOpenInfo = ref(false);

    watch(city, (newValue) => {
      // isOpen.value = true;
      cityName.value = newValue;
      getCoords();
      // console.log(isOpen, 'watch')
    });

    function getCoords() {
      if (cityName.value) {
        axios
          .get(
            `http://api.openweathermap.org/geo/1.0/direct?q=${cityName.value}&limit=10&appid=${apiKey.value}&lang=uk`
          )
          .then((response) => {
            info.value = response.data;
          });
      }
    }

    function selectCity(cityValue) {
      lat.value = cityValue.lat;
      lon.value = cityValue.lon;
      test.value = `Місто ${cityValue.name}, країна ${cityValue.country}`;
      axios
        .get(
          `https://api.openweathermap.org/data/3.0/onecall?lat=${lat.value}&lon=${lon.value}&units=metric&appid=${apiKey.value}&lang=uk`
        )
        .then((response) => {
          inf.value = response;
          console.log(inf.value);
          console.log(isOpen)
          if (inf.value) {
            isOpen.value = false;
            city.value = "";
            isOpenInfo.value = true;
            console.log(inf.value);
          console.log(isOpen)
          }
        });
    }

    return {
      apiKey,
      baseUrl,
      cityName,
      city,
      getCoords,
      info,
      lat,
      lon,
      inf,
      selectCity,
      isOpen,
      test,
      isOpenInfo,
    };
  },
};
</script>

<style scoped>
.v-input {
  text-align: center;
}
input {
  min-width: 200px;
  height: 30px;
  padding: 10px;
  border: 2px solid red;
  font-size: 24px;
  border-radius: 0px 20px;
}
.input-list {
  width: 320px;
  color: rgb(0, 0, 0);
  font-size: 18px;
  margin: 0% auto;
  padding: 5px;
}
.input-list li {
  padding: 5px;
}
.input-list li:hover {
  background: rgb(39, 208, 107);
  border-radius: 0px 20px;
}
</style>
