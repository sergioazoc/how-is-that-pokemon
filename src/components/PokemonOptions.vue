<template>
  <div class="vstack gap-2 col-md-5 mx-auto options-pokemon text-center">
    <div
      v-for="pokemon in pokemons"
      :key="pokemon.id"
      @click="$emit('selectedPokemon', pokemon.id); activeBackground($event);"
      class="selected-pokemon"
      :class="{active: isActive}">{{pokemon.name}}</div>
  </div>
</template>

<script>
export default {
  props: {
    pokemons: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      isActive: false
    }
  },
  methods: {
    activeBackground(e) {
      document.querySelectorAll('.selected-pokemon').forEach((el) => {
        el.classList.remove('active')
      })
      e.target.classList.toggle('active')
    }
  }
}
</script>

<style scoped lang="scss">
.options-pokemon{
  background-color: #e4e4e4;
  padding: 20px;
  border-radius: 10px;
  border: 2px solid #222222;
  .selected-pokemon{
    background-color: #ffffff;
    border: 1px solid #888888;
    border-radius: 5px;
    padding: 5px 0;
    &:hover{
      background-color: #eba016;
      cursor: pointer;
    }
  }
}
.active{
  background-color: #eba016 !important;
}
</style>