<template lang="html">
  <div>
    <li v-on:click="onClick">{{film.title}}</li>
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'film-list-item',
  props: ['film'],
  methods: {
    onClick() {
      eventBus.$emit('selected-film', this.film)
    }
  }
}
</script>

<style lang="css" scoped>

</style>
