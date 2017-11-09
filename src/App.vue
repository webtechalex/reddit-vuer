<template>
  <div id="app">
    <appHeader/>
    <searchInput/>
  </div>
</template>

<script>
  import appHeader from './components/Header.vue';
  import searchInput from './components/SearchInput.vue';

  export default {
    name: 'app',
    components: {
      appHeader, searchInput
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

  .header {
    text-align: center;
    background: mediumseagreen;
    color: white;
    padding: 10px;
    margin-bottom: 10px;
  }

  h1 {
    font-weight: 200;
    margin: 0;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  form {
    width: 320px;
    margin: 0 auto;
    color: mediumseagreen;
  }

  label {
    font-size: 18px;
    margin-right: 10px;
  }

  input {
    width: 230px;
    height: 20px;
  }

  button {
    display: block;
    width: 100px;
    height: 30px;
    margin: 0 auto;
    background: mediumseagreen;
    color: white;
    border: none;
    font-size: 16px;
  }
</style>
