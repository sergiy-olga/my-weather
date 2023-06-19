<template>
  <div>
    <img src="imgUrl" alt="">
  </div>
</template>

<script>
export default {
  name: "v-imgUrl",
  props: { },
  setup() {
    const imgUrl = `https://openweathermap.org/img/wn/${''}@2x.png`
    return {
      imgUrl
    };
  },
};
</script>

<style scoped>

</style>
