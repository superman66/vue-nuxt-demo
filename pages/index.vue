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
      <vue-highcharts :options="options" ref="lineCharts"></vue-highcharts>
    </div>
  </section>
</template>

<script>
import Highcharts from 'highcharts'
import AppLogo from '~/components/AppLogo.vue'

const data = {
  chart: {
    type: 'bar',
  },
  title: {
    text: 'Historic World Population by Region',
  },
  subtitle: {
    text:
      'Source: <a href="https://en.wikipedia.org/wiki/World_population">Wikipedia.org</a>',
  },
  xAxis: {
    categories: ['Africa', 'America', 'Asia', 'Europe', 'Oceania'],
    title: {
      text: null,
    },
  },
  yAxis: {
    min: 0,
    title: {
      text: 'Population (millions)',
      align: 'high',
    },
    labels: {
      overflow: 'justify',
    },
  },
  tooltip: {
    valueSuffix: ' millions',
  },
  plotOptions: {
    bar: {
      dataLabels: {
        enabled: true,
      },
    },
  },
  legend: {
    layout: 'vertical',
    align: 'right',
    verticalAlign: 'top',
    x: -40,
    y: 80,
    floating: true,
    borderWidth: 1,
    backgroundColor:
      (Highcharts.theme && Highcharts.theme.legendBackgroundColor) || '#FFFFFF',
    shadow: true,
  },
  credits: {
    enabled: false,
  },
  series: [
    {
      name: 'Year 1800',
      data: [107, 31, 635, 203, 2],
    },
    {
      name: 'Year 1900',
      data: [133, 156, 947, 408, 6],
    },
    {
      name: 'Year 2012',
      data: [1052, 954, 4250, 740, 38],
    },
  ],
}

export default {
  components: {
    AppLogo,
  },
   data() {
    return {
      options: data,
    }
  }
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
