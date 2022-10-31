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
        <tr v-for="(PokedeView, index) in pokemones" :key="index">
          <td>
            {{ PokedeView.num }}
          </td>
          <td>
            {{ PokedeView.name }}
          </td>
          <td>
            <img v-bind:src="PokedeView.img" alt="" />
            <!-- La directiva v-bind permite enlazar (bindear) una variable 
                                                                  de Vue con un atributo específico de una etiqueta HTML.-->
          </td>
          <td>
            <img
              v-for="(weaknesse, indice) in PokedeView.weaknesses"
              width="50"
              height="50"
              :key="indice"
              :src="typeToIcon(weaknesse)"
              alt=""
            />
          </td>
          <td>
            <img
              v-for="(evolution, indice) in PokedeView.next_evolution"
              width="50"
              height="50"
              :key="indice"
              :src="pokemonToImage(evolution)"
              alt=""
            />
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
  created() {
    console.log(pokemon[0]); /*Sirve para poder hacer pruebas*/
  },
  methods: {
    typeToIcon(weaknesses) {
      return "src/assets/icons/" + weaknesses.toLowerCase() + ".svg";
    },
    pokemonToImage(PokemonEvolution) {
      return pokemon.find((pokemon) => pokemon.num == PokemonEvolution.num).img;
    },
  },
};
</script>

<style>
@media (min-width: 1024px) {
  .pokedex {
    margin-top: 30%;
    margin-bottom: 30%;
    overflow: auto; /* Permite crear el Scrolling*/
    max-height: 70vh;
    align-items: center;
  }
}
</style>
