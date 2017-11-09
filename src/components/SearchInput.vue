<template>
  <form>
    <label>Search:</label>
    <input v-model='searchText'>
    <p>{{ searchText }}</p>
    <button type="submit">Submit</button>
  </form>
</template>

<script>
  export default {
    name: 'searchInput',
    data: function() {
      return {
        searchText: ''
      }
    }
  }
</script>
