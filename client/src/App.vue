<template>
  <div id="app">
    <button v-on:click="toggle='character-viewer'; getCharacters()">View all character</button>
    <button v-on:click="toggle='character-creater'">Create a character</button>
    <CharacterViewer v-show="toggle==='character-viewer'" :characters="characters"/>
    <CharacterCreater v-show="toggle==='character-creater'"/>
  </div>
</template>

<script>
import CharacterViewer from './components/CharacterViewer.vue'
import CharacterCreater from './components/CharacterCreater.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    CharacterViewer,
    CharacterCreater
  },
  data: function() {
    return {
      toggle: 'character-viewer',
      characters: null
    }
  },
  methods: {
    getCharacters: function() {
      axios
        .get('http://localhost:3000/characters')
        .then(response => (this.characters = response.data));
    }
  },
  methed: function() {
    this.getCharacters();
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
