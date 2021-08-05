<template>
  <div v-if="pokemon" class="pt-3">
    <PokemonImage :pokemonId="pokemon.id" :showPokemon="showPokemon" />
    <PokemonOptions :pokemons="pokemonArr" @selected-pokemon="checkAnswer" class="my-3" />

    <div v-if="showAnswer" class="text-center">
      <h2 class="mb-3 answer-pokemon">{{ message }}</h2>
      <button @click="newGame" class="btn btn-success">Nuevo Juego</button>
    </div>

  </div>
  <span v-else class="h1 d-block mx-auto">Loading...</span>
</template>

<script>
// @ is an alias to /src
import PokemonImage from '@/components/PokemonImage.vue'
import PokemonOptions from '@/components/PokemonOptions.vue'
import getPokemonOptions from '@/helpers/getPokemonOptions'

export default {
  name: 'Home',
  components: {
    PokemonImage,
    PokemonOptions
  },
  data() {
    return {
      pokemonArr: [],
      pokemon: null,
      showPokemon: false,
      showAnswer: false,
      message: ''
    }
  },
  methods: {
    async mixPokemonArray() {
      this.pokemonArr = await getPokemonOptions()

      const randomNumber = Math.floor(Math.random() * 4)
      this.pokemon = this.pokemonArr[randomNumber]
    },
    checkAnswer(pokemonId) {
      this.showPokemon = true
      this.showAnswer = true

      if(pokemonId === this.pokemon.id){
        this.message = `Si! es ${this.pokemon.name}`
      }else{
        this.message = `Ops!, era ${this.pokemon.name}`
      }
    },
    newGame() {
      this.pokemonArr   = []
      this.showPokemon  = false
      this.showAnswer   = false
      this.pokemon      = null
      this.mixPokemonArray()
    }
  },
  mounted() {
    this.mixPokemonArray()
  }
}
</script>

<style scoped>
.answer-pokemon{
  color: #ffffff;
}
</style>