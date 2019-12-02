<template lang="html">
  <form v-on:submit.prevent>
    <label for="film">Please select a film:  </label>
    <select v-on:change="handleSelect" v-model="selectedFilm" id="film">

      <option disabled value="">Select a film...</option>
      <option v-for="(film, index) in films" :key="index" v-bind:value="film" >{{film.title}}</option>

    </select>

  </form>
</template>

<script>
import {eventBus} from "../main.js"
export default {
    name: "film-select",
    props: ['films'],
    data(){
      return{
        selectedFilm: {}
      }
    },
    methods:{
    handleSelect(event){
      event.preventDefault();
      eventBus.$emit('selected-film', this.selectedFilm)

    }
  }
  }
</script>

<style lang="css" scoped>
</style>
