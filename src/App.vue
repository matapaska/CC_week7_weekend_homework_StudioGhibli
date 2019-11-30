<template lang="html">
  <div>
    <h3>Studio Ghibli films:</h3>
    <film-select>{{this.films.name}}</film-select>
    <film-description></film-description>

  </div>
</template>

<script>
import FilmSelect from './components/FilmSelect.vue'
import FilmDescription from './components/FilmDescription.vue'

export default {
  name: 'app',
  data(){
    return{
      films: []
    }
  },
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(resp => resp.json())
    .then(data => this.films = data)
  },
  components: {
    "film-select": FilmSelect,
    "film-description": FilmDescription
  }
}
</script>

<style lang="css" scoped>
</style>
