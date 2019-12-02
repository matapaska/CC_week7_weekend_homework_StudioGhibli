<template lang="html">
  <div>
    <GChart class="chart"
    type = "ColumnChart"
    :data="chartData"
    :options="chartOptions"
    />
  </div>

</template>

<script>
import { GChart } from 'vue-google-charts'
export default {
  name: "chart",
  props: ['rottenTomatosScores', 'titles'],
  components: {
    GChart
  },
  data () {
    return {
      chartData: this.titles,
      chartOptions: {
        width: 1000,
        chart: {
          title: 'Rotten tomatoes scores',

        }
      }
    }
  }
}
</script>

<style lang="css" scoped>
</style>
