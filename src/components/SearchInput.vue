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
        console.log(this.text);
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
  }
</style>
