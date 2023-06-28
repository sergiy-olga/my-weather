<template>
  <div class="container">
    <div class="container_logo">
      <div class="logo_weanher">
        <p>my weather</p>
      </div>
      <div class="container-input">
        <v-input v-model="cityName"></v-input>
      </div>
    </div>
  </div>
</template>

<script>
import VInput from "./components/v-input.vue";

export default {
  name: "App",
  components: {
    VInput,
  },
};
</script>

<style>
.container {
  background-image: url("../src/assets/i137674.jpg");
  background-size: cover;
  background-position: center;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  height: 810px;
}
.container-input {
  padding-top: 30px;
}

ul {
  list-style: none;
  padding: 0;
}
.chart{
  background: rgb(252, 253, 250);
}
</style>
