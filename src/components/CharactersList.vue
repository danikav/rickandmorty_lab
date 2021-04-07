<template>
  <section>
      <ul>
          <list-item v-for="(character, index) in characters.results" :character="character" :key="index"> </list-item>
      </ul>
  </section>
</template>

<script>

import ListItem from './ListItem.vue';

export default {
    name: 'characters-list',
    props: ['characters'],
    components: {
        "list-item" : ListItem
    }
}
</script>

<style>

</style>