<script>
import BenderStatistics from './components/BenderStatistics.vue'
export default {
  components: {
    BenderStatistics
  },
  data: () => ({
    count: 10,
    counterTitle: 'Counter Standart',
    incrementAmount: 8,
    characterList: [
      { name: 'Ang', element: ['Air', 'Earth', 'Water', 'Fire'] },
      { name: 'Zuko', element: ['Fire'] },
      { name: 'Toph', element: ['Earth'] },
      { name: 'Katara', element: ['Water'] }
    ],
    newCharacter: {
      name: '',
      element: []
    },
    favoriteList: []
  }),

  methods: {
    addNewCharacter() {
      this.characterList.push(this.newCharacter)
      this.newCharacter = { name: '' }
    },
    favoriteCharacter(character) {
      this.favoriteList.push(character)
      console.log(this.favoriteList)
    }
  }
}
</script>

<template>
  <BenderStatistics :characters="characterList" />
  <h2>Characters</h2>
  <p v-if="characterList.lenght === 0">There are no characters</p>
  <ul>
    <li v-for="(character, index) in characterList" :key="`even-character-${index}`">
      <p>{{ character.name }}<button @click="favoriteCharacter(character)">⭐️ Favorite</button></p>
    </li>
  </ul>
  <h2>Favorite Characters</h2>
  <ul v-if="favoriteList.length > 0">
    <li v-for="(character, index) in favoriteList" :key="`odd-character-${index}`">
      {{ character }}
    </li>
  </ul>
  <p v-else>No favorite characters yet!</p>
  <h2>New character</h2>
  <pre>
        {{ newCharacter }}
      </pre
  >
  <label for="character-name">Name</label>
  <input type="text" v-model="newCharacter.name" @keyup.enter="addNewCharacter" />
  <p>
    <span v-for="(character, index) in characterList" :key="`comma-list-character-${index}`"
      >{{ character.name }}{{ index === characterList.length - 1 ? '' : ', ' }}</span
    >
  </p>
</template>
