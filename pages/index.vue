<template>
  <section class="container">
    <div>
      <app-logo/>
      <h1 class="title">
        vue-nuxt-demo
      </h1>
      <h2 class="subtitle">
        for <a href="https://github.com/superman66/vue-highcharts" target="_blank">vue2-highcharts</a>
      </h2>
      <no-ssr>
      <vue-highcharts :options="options" :highcharts="highcharts" ref="lineCharts"></vue-highcharts>
      </no-ssr>
    </div>
  </section>
</template>

<script>
import Highcharts from 'highcharts'
import Drilldown from 'highcharts/modules/drilldown.js'
import AppLogo from '~/components/AppLogo.vue'

const DrilldownData = {
  chart: {
    type: 'column',
  },
  title: {
    text: 'Basic drilldown',
  },
  xAxis: {
    type: 'category',
  },
  legend: {
    enabled: false,
  },
  plotOptions: {
    series: {
      borderWidth: 0,
      dataLabels: {
        enabled: true,
      },
    },
  },
  series: [
    {
      name: 'Things',
      colorByPoint: true,
      data: [
        {
          name: 'Animals',
          y: 5,
          drilldown: 'animals',
        },
        {
          name: 'Fruits',
          y: 2,
          drilldown: 'fruits',
        },
        {
          name: 'Cars',
          y: 4,
          drilldown: 'cars',
        },
      ],
    },
  ],
  drilldown: {
    series: [
      {
        id: 'animals',
        data: [
          ['Cats', 4],
          ['Dogs', 2],
          ['Cows', 1],
          ['Sheep', 2],
          ['Pigs', 1],
        ],
      },
      {
        id: 'fruits',
        data: [
          {
            name: 'Apples',
            y: 4,
          },
          {
            name: 'Oranges',
            y: 2,
            drilldown: 'third-leves',
          },
        ],
      },
      {
        id: 'cars',
        data: [['Toyota', 4], ['Opel', 2], ['Volkswagen', 2]],
      },
      {
        id: 'third-leves',
        data: [['Toyota', 4], ['Opel', 2], ['Volkswagen', 2]],
      },
    ],
  },
}

export default {
  components: {
    AppLogo,
  },
  data() {
    return {
      options: DrilldownData,
      highcharts: Highcharts,
    }
  },
  mounted() {
    Drilldown(Highcharts)
    Highcharts.setOptions({
      lang: {
        drillUpText: 'back',
      },
    })
  },
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
