<template>
  <form v-on:submit="searchSubmit">
    <label>Search:</label>
    <input v-model='searchText'>
    <p>{{ searchResult }}</p>
    <button type="submit">Submit</button>
  </form>
</template>

<script>
  export default {
    name: 'searchInput',
    data: function() {
      return {
        searchText: '',
        searchResult: ''
      }
    },
    methods: {
      searchSubmit: function(event) {
        event.preventDefault();
        this.searchResult = event.target[0].value;
      }
    }
  }
</script>
