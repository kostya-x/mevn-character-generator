<template>
  <div class="character-creater">
    <h1>Character Creater</h1>
    <label for="character-name">Character Name: </label>
    <input type="text" id="character-name" v-model="name" placeholder="Enter a name">
    <label for="profession-list">Character Profession: </label>
    <select id="profession-list" v-model="profession">
      <option value="Warrior">Warrior</option>
      <option value="Rouge">Rouge</option>
      <option value="Mage">Mage</option>
      <option value="Cliric">Cliric</option>
    </select>
    <button v-on:click="postCharacter">Create Character</button>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'CharacterCreater',
  data: function() {
    return {
      name: "",
      profession: ""
    }
  },
  methods: {
    postCharacter: function() {
      axios
        .post('http://localhost:3000/characters', {
          name: this.name,
          profession: this.profession
        });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
