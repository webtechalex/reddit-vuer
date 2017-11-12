<template>
  <div>
    <form>
      <label>Search:</label>
      <input v-model="text">
      <button v-on:click="searchSubmit">Submit</button>
    </form>
  </div>
</template>

<script>
  export default {
    name: 'searchInput',
    data: function() {
      return {
        text: ''
      }
    },
    methods: {
      searchSubmit: function(e) {
        e.preventDefault();
        this.$emit('search:submit', this.text);
        this.text = '';
      }
    }
  }
</script>

<style>
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
    margin: 10px auto;
    background: mediumseagreen;
    color: white;
    border: none;
    font-size: 16px;
    outline: none;
    box-shadow: lightgray 2px 2px 2px;
  }
  button:active {
    background: darkseagreen;
    position: relative;
    top: 1px;
    left: 1px;
    box-shadow: lightgray 1px 1px 1px;
  }
</style>
