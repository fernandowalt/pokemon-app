<template>
  <div class="h-screen bg-gradient-to-r from-indigo-500 w-full flex items-center justify-center ">
    <pokemonPages />
  </div>
</template>

<script>
import PokemonPages from "./pages/PokemonPages.vue";

export default {
  name: "App",
  components: {
    PokemonPages,
  },
};
</script>


