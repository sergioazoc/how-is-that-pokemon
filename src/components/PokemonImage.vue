<template>
  <div class="bg-pokemon ratio ratio-16x9">
    <div class="d-flex align-items-center">

    <img :class="{'hide-pokemon': !showPokemon}" class="img-pokemon" :src="imgSrc" alt="pokemon">
    </div>
  </div>
</template>

<script>
export default {
  props: {
    pokemonId: {
      type: Number,
      required: true
    },
    showPokemon: {
      type: Boolean,
      required: true,
      default: false
    }
  },
  computed: {
    imgSrc(){
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`
    }
  }
}
</script>

<style scoped>
.img-pokemon{
  max-height: 100%;
  width: auto;
  padding: 12% 0 12% 19%;
}
.hide-pokemon{
  filter: brightness(0);
  user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  -webkit-user-drag: none;
  -webkit-user-select: none;
}
.bg-pokemon{
  background-image: url('https://images3.alphacoders.com/677/677583.png');
  background-size: cover;
  background-position: center;
  border-radius: 20px;
  border: 4px solid #ffcb05;
}
</style>