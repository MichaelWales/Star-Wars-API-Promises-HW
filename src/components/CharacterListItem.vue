<template lang="html">
  <li>{{character.name}} <br> {{character.height}}cm tall</li>
</template>

<script>
export default {
  name: 'character-list-item',
  props: ['character']
}
</script>

<style lang="css" scoped>

  li {
    color: yellow;
    padding-top: 10px;
  }

</style>
