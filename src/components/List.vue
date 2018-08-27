<template>
  <section>
    <h2>Pokemon Colors</h2>
    <div>
      <ColorSearch :onSearch="handleSearch"/>
      <ul v-if="colors">
        <Pokemon v-for="color in colors"
          :key="color.id"
          :color="color"/>
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
      colors: null,
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
      this.searchColor();
    },
    searchColor() {
      api.getColors(this.search)
        .then(response => {
          this.colors = response.results;
          this.total = response.count;
        });
    }
  }
};
</script>

<style>

</style>
