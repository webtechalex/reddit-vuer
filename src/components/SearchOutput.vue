<template>
  <div class="result-container">
    <ul>
      <li v-for="result in searchResults" v-bind:result="result">{{ result.title }}<p>{{ result.selftext }}</p><a v-bind:href="result.url">{{ result.url }}</a></li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'searchOutput',
    props: ['searchResults']
  }
</script>

<style>
  .result-container {
    width: 400px;
    margin: 0 auto;
  }
  li {
    margin: 20px 0;
    border: 1px solid lightgray;
    padding: 5px;
  }
</style>
