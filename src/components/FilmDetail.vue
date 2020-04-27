<template lang="html">
  <div>
    <div>
      <ul>
        <h2 id="film-detail-title">{{film.title}}</h2>
        <h3>Film Number <br> {{film.episode_id}}</h3>
        <h3>Opening Date <br> {{film.release_date}}</h3>
        <h3>Directed By <br> {{film.director}}</h3>
      </ul>
    </div>

    <div>
      <character-list id="character-list" v-if="characters.length" :characters="characters"></character-list>
    </div>
  </div>
</template>

<script>
import {eventBus} from '../main.js';
import CharacterList from './CharacterList.vue';
import CharacterListItem from './CharacterListItem.vue';

export default {
  name: 'film-detail',
  props: ['film'],
  data() {
    return {
      characters: []
    }
  },
  components: {
    'character-list': CharacterList
  },
  mounted() {
    this.getCharacters()
  },
  watch: {
    film: function() {
      this.getCharacters()
    }
  },
  methods: {
    getCharacters() {
      const characterPromises = this.film.characters.map((characterURL) => {
        return fetch(characterURL).then(response => response.json());
      })
      Promise.all(characterPromises)
      .then((data) => {
        this.characters = data;
      })
    }
  }
}
</script>

<style lang="css" scoped>

  #film-detail-title {
    color: yellow;
    font-family: 'Libre Franklin', sans-serif;
    font-weight: 700;
    font-size: 24px;
  }

  h3 {
    color: yellow;
    font-family: 'Libre Franklin', sans-serif;
    font-weight: 500;
    font-size: 20px;
  }

  ul {
    color: yellow;
    text-align: right;
    position: absolute;
    right: 100px;
    top: 121px;
  }

  #character-list {
    text-align: center;
    color: yellow;
    font-family: 'Libre Franklin', sans-serif;
    font-weight: 700;
    font-size: 24px;
  }

</style>
