<template lang="html">
  <div>
    <br>
    <h2>Film List</h2>
    <ul>
      <film-list-item id="list-item" v-for="(film, index) in films" :film="film" :key="index"></film-list-item>
    </ul>
  </div>
</template>

<script>
import FilmListItem from './FilmListItem.vue';

export default {
  name: 'film-list',
  props: ['films'],
  components: {
    'film-list-item': FilmListItem
  }
}
</script>

<style lang="css" scoped>

  #list-item {
    list-style-position: inside;
    list-style: none;
    text-align: left;
    margin-top: 15px;
    font-size: 20px;
    font-family: 'Libre Franklin', sans-serif;
    font-weight: 500;
  }

</style>
