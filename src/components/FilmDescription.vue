<template lang="html">
  <div v-if="film">
    <h3>{{film.title}}</h3>
    <p>{{film.director}}</p>
    <p>{{film.release_date}}</p>
    <p>{{film.description}}</p>
  </div>
</template>

<script>
import {eventBus} from "../main.js"
export default {
    name: "film-description",
    data(){
      return{
      film: []
      }
    },
    mounted(){
      eventBus.$on('selected-film', payload => {
        this.film = payload;
      })
    }
  }
</script>

<style lang="css" scoped>
</style>
