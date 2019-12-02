<template >
  <div>
    <h2>Welcome to Studio Ghibli</h2>
    <film-select :films="films"></film-select>
    <br>
    <film-description></film-description>
    <br>
    <chart :rottenTomatosScores="rottenTomatosScores" :titles="titles"></chart>

  </div>
</template>

<script>
import {eventBus} from "./main.js"
import FilmSelect from './components/FilmSelect.vue'
import FilmDescription from './components/FilmDescription.vue'
import Chart from './components/Chart.vue'

export default {
  name: 'app',
  data(){
    return{
      films: [],
      selectedFilm: "",
      rottenTomatosScores: [],
      titles: [["title", "RT_score"]],
      titleRTScore: []
    }
  },
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(resp => resp.json())
    .then(data => this.films = data)
    .then(() => this.getTitle())
    .then(() => this.getRTScore())
    // .then(() => this.titleRTScore())

    eventBus.$on('selected-film', payload => {
      this.selectedFilm = payload;
    })
  },
  components: {
    "film-select": FilmSelect,
    "film-description": FilmDescription,
    "chart": Chart
  },

  methods:{
    getTitle: function () {
      const getTitles = this.films.forEach((object) => {
          this.titles.push([object.title, Number(object.rt_score)])
        }
      )
    },

    getRTScore: function () {
      const getScore = this.films.forEach((object) => {
          this.rottenTomatosScores.push(object.rt_score)
        }
      )
    },

    getTitleRTScore: function () {
      const getBoth = titles.map((el, i) => {
      return [titles[i], rottenTomatosScores[i]]})
      var output = Object.fromEntries(getBoth)
    }
  }
}
</script>

<style lang="css" scoped>
body{
  background-image: url('../public/Totoro.jpeg');
}

</style>
