<template>
  <transition name="fade">
    <div v-if="inputIsInvalid" class="validation">
      <h2>Invalid Input</h2>
      <p>Please enter a search term...</p>
    </div>
  </transition>
</template>

<script>
  export default {
    name: 'validation',
    props: ['inputIsInvalid']
  }
</script>

<style>
  .validation {
    width: 400px;
    margin: 0 auto;
    border: 1px solid darkorange;
    color: darkorange;
    padding: 10px;
    box-sizing: border-box;
    text-align: center;
  }
  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s
  }
  .fade-enter, .fade-leave-to {
    opacity: 0
  }
</style>
