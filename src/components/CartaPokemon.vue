<!-- CartaPokemon.vue -->
<template>
  <div class="carta-pokemon">
    <div class="pokemon-imagen">
      <img :src="imagenPokemon" :alt="poke.name" :class="{ descubierto: descubierto }" />
      <form v-if="!descubierto" @submit.prevent="handleSubmit">
        <input v-model="namePoke" type="text" />
        <button>Descubrir</button>
      </form>
      <p v-else>{{ poke.name }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "CartaPokemon",
  props: {
    poke: Object,
  },
  data() {
    return {
      namePoke: "",
      descubierto: false,
    };
  },
  computed: {
    imagenPokemon() {
      // Verificar si la ruta a la imagen oficial está disponible
      return this.poke.sprites.other?.["official-artwork"]?.front_default || this.poke.sprites.front_default;
    }
  },
  methods: {
    handleSubmit() {
      if (this.namePoke.toLowerCase() === this.poke.name.toLowerCase()) {
        this.descubierto = true;
        this.$emit('pokemon-descubierto');
      } else {
        alert("Nombre incorrecto, intenta de nuevo.");
      }
    }
  }
};
</script>

<style scoped>
.carta-pokemon {
  border: 2px solid #f5f5f5;
  border-radius: 10px;
  width: 250px;
  text-align: center;
  background-color: #fff;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  overflow: hidden;
  background-color: #f7f7f7;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.carta-pokemon:hover {
  transform: scale(1.05);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.3);;
}

.pokemon-imagen {
  padding: 10px;
  

}

img {
  width: 100px;
  height: 100px;
  object-fit: cover;
  filter: blur(5px) grayscale(100%);
  transition: filter 0.3s ease;
}

img.descubierto {
  filter: none;
}

form {
  margin: 10px 0;
}

input[type="text"] {
  padding: 5px;
  border: 1px solid #ddd;
  border-radius: 5px;
  margin-bottom: 10px;
  font-size: 16px;
}

button {
  background-color: #ffcb05;
  color: #fff;
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #f2a20e;
}

p {
  font-size: 18px;
  font-weight: bold;
  color: #333;
  margin: 10px 0;
}
</style>
