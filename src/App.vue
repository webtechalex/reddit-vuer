<template>
  <div id="app">
    <appHeader></appHeader>
    <searchInput v-on:search:submit="searchSubmit"></searchInput>
    <searchOutput :text="text"></searchOutput>
  </div>
</template>

<script>
  import appHeader from './components/Header.vue';
  import searchInput from './components/SearchInput.vue';
  import searchOutput from './components/SearchOutput.vue';

  export default {
    name: 'app',
    data: function() {
      return {
        text:''
      }
    },
    methods: {
      searchSubmit: function(text) {
        this.text = text
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
