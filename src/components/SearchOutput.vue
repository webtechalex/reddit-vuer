<template>
  <div class="result-container">
    <p>{{ text }}</p>
  </div>
</template>

<script>
  export default {
    name: 'searchOutput',
    props: ['text']
  }
</script>

<style>
  .result-container {
    width: 400px;
    margin: 0 auto;
  }
</style>
