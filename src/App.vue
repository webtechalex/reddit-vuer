<template>
  <div id="app">
    <appHeader></appHeader>
    <searchInput v-on:search:submit="searchSubmit"></searchInput>
    <searchOutput :searchResults="resultsArray"></searchOutput>
  </div>
</template>

<script>
  import axios from 'axios';

  import appHeader from './components/Header.vue';
  import searchInput from './components/SearchInput.vue';
  import searchOutput from './components/SearchOutput.vue';

  export default {
    name: 'app',
    data: function() {
      return {
        text:'',
        searchResults: null
      }
    },
    computed: {
      resultsArray: function() {
        return (this.searchResults) ? this.searchResults.data.data.children.map((result, index) => ({
          title: result.data.title,
          selftext: result.data.selftext,
          url: result.data.url,
          id: result.data.id
        })) : [];
      }
    },
    methods: {
      searchSubmit: function(text) {
        let app = this;

        axios.get('https://www.reddit.com/r/' + text + '.json')
          .then(function (response) {
            app.searchResults = response;
          })
          .catch(function(err) {
            console.log(err);
          });
      }
    },
    components: {
      appHeader, searchInput, searchOutput
    }
  }
</script>

<style>
  body {
    margin: 0;
    color: mediumseagreen;
  }

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
  }

  h1 {
    font-weight: 200;
    margin: 0;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }
</style>
