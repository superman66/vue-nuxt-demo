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

      <no-ssr>
      <vue-highcharts :options="mapOptions" :highcharts="highcharts" ref="mapCharts"></vue-highcharts>
      </no-ssr>
    </div>
  </section>
</template>

<script>
import Highcharts from 'highcharts/highmaps'
import Drilldown from 'highcharts/modules/drilldown.js'
import AppLogo from '~/components/AppLogo.vue'
import { DrilldownOptions, MapData} from '~/static/data.js'


export default {
  components: {
    AppLogo,
  },
  data() {
    return {
      options: DrilldownOptions,
      mapOptions: {
        title: {
          text: 'Habitat of the Rusty Blackbird',
        },

        subtitle: {
          text:
            'An example of a distribution map in Highcharts.<br/>' +
            'Source: <a href="http://en.wikipedia.org/wiki/File:Euphagus_carolinus_map.svg">Wikipedia</a>.',
        },

        plotOptions: {
          series: {
            tooltip: {
              headerFormat: '',
              pointFormat: '{series.name} area',
            },
          },
        },

        legend: {
          align: 'left',
          backgroundColor:
            (Highcharts.theme && Highcharts.theme.legendBackgroundColor) ||
            'rgba(255, 255, 255, 0.85)',
          floating: true,
          layout: 'vertical',
          verticalAlign: 'bottom',
          reversed: true,
        },
        series: MapData,
      },
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
