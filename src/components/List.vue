<template>
  <section>
      <h2>Search Your favorite Poke-Color</h2>
      <ColorSearch :onSearch="handleSearch"/>

      <Loader :loading="loading"/>

      <pre v-show="error">
        {{error}}
      </pre>

      <div>
        <ul v-if="allPokemon">
          <Pokemon v-for="pokemon in allPokemon"
            :key="pokemon.name"
            :pokemon="pokemon"/>
        </ul>
      </div>

  </section>

</template>

<script>
import Pokemon from './Pokemon';
import api from '../services/api';
import ColorSearch from './ColorSearch';
import Loader from './Loader';
export default {
  data() {
    return {
      allPokemon: null,
      search: '',
      loading: false,
      error: null,
      total: 0
    };
  },
  components: {
    Pokemon,
    ColorSearch,
    Loader
  },
  methods: {
    handleSearch(search) {
      this.search = search;
      this.searchPokemon();
    },
    searchPokemon() {
      this.loading = true;
      this.error = null;

      api.getAllPokemon(this.search)
        .then(response => {
          console.log('did you make it', response);
          this.allPokemon = response.pokemon_species;
          this.total = response.count;
          this.loading = false;
        })
        .catch(err => {
          this.error = err.message;
          this.loading = false;
        });
    }
  }
};
</script>

<style>
ul {
  display:grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); 
  list-style-type: none;
}
</style>
