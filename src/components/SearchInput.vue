<template>
  <div class="searchWrapper">
    <input id="search"
           class="search"
           v-model="searchValue"
           @input="handleInput"
    >
  </div>
</template>

<script>
import debounce from 'lodash.debounce';
import axios from 'axios';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'SearchInput',
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },
  methods: {
    // eslint-disable-next-line
    handleInput: debounce(function () {
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
          console.log(this.results);
        }).catch((error) => {
          console.log(error);
        });
    }, 500),
  },
};
</script>

<style scoped>
  .searchWrapper {
    display: flex;
    flex-direction: column;
    width: 300px;
    margin-top: 50px;
  }

  label {
    font-family: Montserrat, sans-serif;
  }

  input {
    height: 30px;
    border: 0;
    border-bottom: 1px solid black;
    background: none;
  }
</style>
