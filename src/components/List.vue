<template>
  <section>
    <h2>Pokemon Colors</h2>
    <div>
      <ColorSearch :onSearch="handleSearch"/>
      <ul v-if="allPokemon">
        <Pokemon v-for="name in allPokemon"
          :key="name.id"
          :name="name"/>
      </ul>
    </div>
  </section>

</template>

<script>
import Pokemon from './Pokemon';
import api from '../services/api';
import ColorSearch from './ColorSearch';
export default {
  data() {
    return {
      allPokemon: null,
      search: '',
      total: 0
    };
  },
  components: {
    Pokemon,
    ColorSearch
  },
  methods: {
    handleSearch(search) {
      this.search = search;
      this.searchPokemon();
    },
    searchPokemon() {
      api.getAllPokemon(this.search)
        .then(response => {
          console.log('did you make it', response);
          this.allPokemon = response.pokemon_species;
          this.total = response.count;
        });
    }
  }
};
</script>

<style>

</style>
