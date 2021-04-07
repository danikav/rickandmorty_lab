<template>
  <div id="app">
    <h1>Characters</h1>
    <section>
      <characters-list :characters='characters'></characters-list>
    </section>
  </div>
</template>

<script>

import CharactersList from './components/CharactersList.vue'

export default {
  name: 'App',
  data(){
    return{
      characters: [],
      selectedCharacter: null,
      new_characters: []
      // url = 'https://rickandmortyapi.com/api/character/'
    }
  },

  mounted() {
    // fetch('https://rickandmortyapi.com/api/character/')
    // .then(res => res.json())
    // .then(characters => this.characters = characters)
    // fetch(this.characters.info.next)
    // .then(res => res.json())
    // .then(characters => this.new_characters = characters)
  let url = 'https://rickandmortyapi.com/api/character/'
    while (url) {
      fetch(url)
      .then(res => res.json())
      .then(responseData => {
        this.characters.push(...responseData.results)
        url = responseData.info.next
      })
      
  // this.fetchCharacters()
  }
  },

    // fetchCharacters: function() {
    
    //  let url = 'https://rickandmortyapi.com/api/character/';

    //  do {
    //    const res = await fetch(url);
    //    const data = await res.json();
    //    url = data.next;
    //    characters.push(...data.characters);
    //  } while(url)
    // let url = 'https://rickandmortyapi.com/api/character/'
    // while (url.info.next !== null) {
    //   fetch(url)
    //   .then(res => res.json)
    //   .then(characters => this.characters.push(characters))
    //   url = url.info.next
    // }
    
  components: {
  "characters-list": CharactersList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
