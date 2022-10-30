<!-- eslint-disable vue/valid-attribute-name -->
<!-- eslint-disable vue/no-parsing-error -->
<template>
  <div class="pokedex">
    <table class="table table-dark">
      <thead>
        <tr>
          <th>#</th>
          <th>Nombre</th>
          <th>Imagen</th>
          <th>Debilidades</th>
          <th>Evoluciones</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(pokemon, index) in pokemones" :key="index">
          <td>
            {{ pokemones[index]["num"] }}
          </td>
          <td>
            {{ pokemones[index]["name"] }}
          </td>
          <td>
            <img src="http://www.serebii.net/pokemongo/pokemon/002.png" alt="">
          </td>
          <td>
            {{ pokemones[index]["weaknesses"] }}
          </td>
          <td>
            {{ pokemones[index]["next_evolution"] }}
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { pokemon } from "../datasets/pokemon.json";
export default {
  name: "PokedexView",
  data() {
    return {
      pokemones: pokemon,
    };
  },
  methods: {
    display_image(src) {
      var a = new Image();
      a.src = src;
      return a;
    },
  },
};
</script>

<style>
@media (min-width: 1024px) {
  .pokedex {
    margin-top: 30%;
    margin-bottom: 30%;
    overflow: auto;
    max-height: 70vh;
    align-items: center;
  }
}
</style>
