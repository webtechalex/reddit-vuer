<template>
  <div id="app">
    <appHeader></appHeader>
    <searchInput v-on:search:submit="searchSubmit"></searchInput>
    <validation v-bind:inputIsInvalid="inputIsInvalid"></validation>
    <responseError v-bind:responseError="responseError"></responseError>
    <searchOutput :searchResults="resultsArray"></searchOutput>
  </div>
</template>

<script>
  import axios from 'axios';

  import appHeader from './components/Header.vue';
  import searchInput from './components/SearchInput.vue';
  import searchOutput from './components/SearchOutput.vue';
  import validation from './components/InputValidation.vue';
  import responseError from './components/ResponseError.vue'

  export default {
    name: 'app',
    data: function() {
      return {
        text:'',
        searchResults: null,
        inputIsInvalid: false,
        responseError: false
      }
    },
    computed: {
      resultsArray: function() {
        return (this.searchResults) ? this.searchResults.data.data.children.map((result, index) => ({
          title: result.data.title,
          selftext: result.data.selftext.length ? result.data.selftext.substr(0, 198) + '...' : '',
          url: result.data.url,
          id: result.data.id
        })) : [];
      }
    },
    methods: {
      searchSubmit: function(text) {
        let app = this;
        this.searchResults = null;
        this.responseError = null;
        if (text === '') {
          this.inputIsInvalid = true;
        } else {
          this.inputIsInvalid = false;
          axios.get('https://www.reddit.com/r/' + text + '.json')
            .then(function (response) {
              app.searchResults = response;
              app.text = '';
            })
            .catch(function (err) {
              app.responseError = true;
            });
        }
      }
    },
    components: {
      appHeader, searchInput, searchOutput, validation, responseError
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
