<template>
  <div class="mx-8">
    <img :src="imgSrc" alt="pokemon" :class="cambiarClase()" />
  </div>
</template>

<script>
export default {
  props: {
    pokemonId: {
      type: Number,
      required: true,
    },
    showPokemon: {
      type: Boolean,
      required: true,
      default: false,
    },
  },

  computed: {
    imgSrc() {
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`;
    },
  },

  methods: {
    cambiarClase() {
      return !this.showPokemon ? "hidden-pokemon" : "";
    },
  },
};
</script>

<style scoped>
.hidden-pokemon {
  filter: brightness(0);
}

img{
  height: 250px;
  width: 250px;
}
</style>