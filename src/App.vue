<!-- App.vue -->
<template>
  <div class="container">
    <img
      src="../public/logo-poke.jpg"
      alt="logo-pokemon"
      class="logo-pokemon"
    />
    <h1>¿Quien es este pokemon?</h1>
    <h2>Pokémon descubiertos: {{ pokemonsDescubiertos }}</h2>

    <div class="pokemones">
      <CartaPokemon
        v-for="(pokemon, index) in pokemonList"
        :key="index"
        :poke="pokemon"
        @pokemon-descubierto="incrementarContador"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import CartaPokemon from "./components/CartaPokemon.vue";

export default {
  name: "App",
  components: {
    CartaPokemon,
  },
  data() {
    return {
      pokemonList: [],
      pokemonsDescubiertos: 0,
    };
  },
  methods: {
    async getPokemon() {
      const URL_BASE = "https://pokeapi.co/api/v2/pokemon?limit=20";
      try {
        const responseApi = await axios.get(URL_BASE);
        const primerLlamado = responseApi.data.results;

        const pokemonResponse = await Promise.all(
          primerLlamado.map(async (pokemon) => {
            const { data } = await axios.get(pokemon.url);
            return data;
          })
        );

        return pokemonResponse;
      } catch (error) {
        console.error(error);
      }
    },
    incrementarContador() {
      this.pokemonsDescubiertos++;
    },
  },
  async mounted() {
    this.pokemonList = await this.getPokemon();
  },
};
</script>

<style scoped>
h1 {
  text-align: center;
}
.pokemones {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
}
.logo-pokemon {
  width: 20rem;
  height: 15rem;
}
.container {
  text-align: center;
}
</style>
