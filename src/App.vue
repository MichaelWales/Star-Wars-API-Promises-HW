<template lang="html">
  <div id="app">
    <h1>Star Wars n' Stuff</h1>

    <film-list id="film-list" :films="films"></film-list>

    <film-detail v-if="selectedFilm" :film="selectedFilm"></film-detail>
  </div>
</template>

<script>
import {eventBus} from './main.js';
import FilmList from './components/FilmList.vue';
import FilmListItem from './components/FilmListItem.vue';
import FilmDetail from './components/FilmDetail.vue';

export default {
  name: 'app',
  data() {
    return {
      films: [],
      selectedFilm: null
    }
  },
  mounted() {
    fetch('https://swapi.dev/api/films/')
    .then(response => response.json())
    .then(data => this.films = data.results)

    eventBus.$on('selected-film', (film) => {
      this.selectedFilm = film
    })
  },
  components: {
    'film-list': FilmList,
    'film-list-item': FilmListItem,
    'film-detail': FilmDetail
  }
}
</script>

<style lang="css" scoped>

  h1 {
    text-align: center;
    color: yellow;
    font-family: 'Libre Franklin', sans-serif;
    font-weight: 900;
  }

  #app {
    padding: 30px;
    background-image: url(https://us.123rf.com/450wm/markusgann/markusgann1704/markusgann170400103/78663156-2d-illustration-of-a-seamless-stars-background.jpg?ver=6);
  }

  #film-list {
    text-align: left;
    color: yellow;
    font-family: 'Libre Franklin', sans-serif;
    font-weight: 700;
  }

</style>
