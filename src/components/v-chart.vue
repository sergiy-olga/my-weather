<template>
  <div>
    <canvas ref="myChart"></canvas>
    <p>
      {{
        new Date(
          weatherChart.data?.hourly[0].dt * 1000 -
            weatherChart.data?.timezone_offset
        ).getHours()
      }}
    </p>
    <p>
      {{
        new Date(
          weatherChart.data?.hourly[1].dt * 1000 -
            weatherChart.data?.timezone_offset
        )
      }}
    </p>
    <!-- <p>{{ weatherChart.data?.hourly }}</p> -->
  </div>
</template>

<script>
import { Chart } from "chart.js/auto";
import { onMounted, ref, toRef, toRefs, watch } from "vue";
export default {
  name: "v-chart",
  props: {weatherChart: Object},
  setup(props) {
    const chart = {};
    const myChart = ref(null);
    const labels = "";
    const hourlys = toRef(props, 'weatherChart');
    const { weatherChart } = toRefs(props)
    const data = [
      { year: 2010, count: 10 },
      { year: 2011, count: 20 },
      { year: 2012, count: 15 },
      { year: 2013, count: 25 },
      { year: 2014, count: 22 },
      { year: 2015, count: 30 },
      { year: 2016, count: 28 },
    ];


    function initChart() {
      chart.value = new Chart(myChart.value, {
        type: "bar",
        data: {
          labels: data.map((row) => row.year),
          datasets: [
            {
              label: "Acquisitions by year",
              data: data.map((row) => row.count),
              borderColor: "red",
              borderWidth: 2,
              backgroundColor: "green",
            },
          ],
        },
      });
      console.log(props.weatherChart)
    }

    onMounted(() => initChart());
    watch(props.weatherChart, (oldValue) =>{
      console.log(oldValue)
    })
    console.log(weatherChart.value)

    return {
      data,
      chart,
      initChart,
      myChart,
      labels,
      hourlys
    };
  },
};
</script>

<style scoped>
</style>
