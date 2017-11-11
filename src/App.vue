<template>
  <div id="app">
    <appHeader></appHeader>
    <searchInput v-on:search:submit="searchSubmit"></searchInput>
    <searchOutput :searchResults="searchResults"></searchOutput>
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
    methods: {
      searchSubmit: function(text) {
        let app = this;

        axios.get('https://www.reddit.com/r/' + text + '.json')
          .then(function (response) {
//            console.log(response.data.data.children);
            const rawData = response.data.data.children;
            const responseArray = Array.from(rawData).map((item, index) => {
              return {
                title: rawData[index].data.title,
                selftext: rawData[index].data.selftext,
                url: rawData[index].data.url
              };
            });
            app.searchResults = responseArray;
            console.log(app.searchResults);
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
