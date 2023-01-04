<template>
  <div>
    <p>This is a test</p>
  </div>
  <div>
    <ul>
      <li v-for="(pokemon, index) in pokemons.results" :key="index"> {{pokemon.name}} </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'App',
  data() {
    return {
      pokemons: [],
    };
  },
  created() {
    this.getUser();
  },
  methods: {
    getUser() {
      axios
        .get("https://pokeapi.co/api/v2/pokemon?limit=20")
        .then((res) => {
          this.pokemons = res.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style>
</style>
