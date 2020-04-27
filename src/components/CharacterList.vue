<template lang="html">
  <div>
    <br>
    <h3>Cast</h3>
    <character-list-item id="character-list-item" v-for="(character, index) in characters" :character="character" :key="index"></character-list-item>
  </div>
</template>

<script>
import CharacterListItem from './CharacterListItem.vue';

export default {
  name: 'character-list',
  props: ['characters'],
  components: {
    'character-list-item': CharacterListItem
  }
}
</script>

<style lang="css" scoped>

  #character-list-item {
    list-style-position: inside;
    list-style: none;
    text-align: center;
    margin-top: 15px;
    font-size: 20px;
    font-family: 'Libre Franklin', sans-serif;
    font-weight: 500;
  }

</style>
