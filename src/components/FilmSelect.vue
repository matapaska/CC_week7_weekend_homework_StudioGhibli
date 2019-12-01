<template lang="html">
  <form>
    <select>
      <option v-for="(film, index) in films" :key="index" v-bind:film="film">{{film.title}}</option>

    </select>

  </form>
</template>

<script>
export default {
    name: "film-select",
    props: ['films']
  }
</script>

<style lang="css" scoped>
</style>
