<template>
  <h1 v-if="!pokemon">Espere por favor...</h1>
  <div class="text-center" v-else>
    <div class="mb-2 text-purple-800 text-2xl font-bold capitalize">
      ¿que pokemon soy?
    </div>
    <PokemonImages :pokemonId="pokemon.id" :showPokemon="showPokemon" />
    <PokemonOptions :pokemons="pokemonsArr" @selection="checkAnswer" />
    <h2>{{ message }}</h2>
    <button
      class="bg-purple-700 py-1 px-2 rounded mt-1 text-white"
      @click="reiniciar"
    >
      Nuevo Juego
    </button>
  </div>
</template>

<script>
import PokemonImages from "@/components/PokemonImage.vue";
import PokemonOptions from "@/components/PokemonOptions.vue";
import getPokemonOptions from "@/helpers/getPokemonOptions";

export default {
  components: {
    PokemonImages,
    PokemonOptions,
  },
  data() {
    return {
      pokemonsArr: [],
      pokemon: null,
      showPokemon: false,
      showAnswer: false,
      message: "",
    };
  },

  methods: {
    async mixPokemonArr() {
      this.pokemonsArr = await getPokemonOptions();
      const numeroAleatorio = Math.floor(Math.random() * 4);
      this.pokemon = this.pokemonsArr[numeroAleatorio];
    },

    checkAnswer(selectedPokemon) {
      if (selectedPokemon === this.pokemon.id) {
        this.message = `Correcto!! es ${this.pokemon.name}`;
        this.showPokemon = true;
      } else {
        this.message = `Oops, es ${this.pokemon.name}`;
      }
    },

    reiniciar() {
      this.showPokemon = false;
      this.showAnswer = false;
      this.pokemon = null;
      this.pokemonsArr = false;
      this.mixPokemonArr();
    },
  },

  mounted() {
    this.mixPokemonArr();
  },
};
</script>

