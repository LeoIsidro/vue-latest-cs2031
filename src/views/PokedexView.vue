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
        <tr
          v-for="(PokedexView, index) in pokemones"
          :key="index"
          :num="PokedexView.num"
          :name="PokedexView.name"
          :img="PokedexView.img"
          :weaknesses="PokedexView.weaknesses"
          :nextEvolution="PokedexView.next_evolution"
        >
          <td>
            {{ num }}
          </td>
          <td>
            {{ name }}
          </td>
          <td>
            <img v-bind:src="img" alt="" />
            <!-- La directiva v-bind permite enlazar (bindear) una variable 
                                                                  de Vue con un atributo específico de una etiqueta HTML.-->
          </td>
          <td>
            <img
              v-for="(weaknesse, indice) in weaknesses"
              width="50"
              height="50"
              :key="indice"
              :src="typeToIcon(weaknesses)"
              alt=""
            />
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
  props: ["num", "name", "img", "weaknesses", "nextEvolution"],
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
      return pokemon.find(
        (PokedexView) => PokedexView.num == PokemonEvolution.num
      ).img;
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
