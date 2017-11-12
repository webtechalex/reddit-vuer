<template>
  <transition name="fade">
    <div v-if="responseError" class="validation">
      <h2>Error</h2>
      <p>Please try another search term...</p>
    </div>
  </transition>
</template>

<script>
  export default {
    name: 'responseError',
    props: ['responseError']
  }
</script>

<style>
  .validation {
    width: 400px;
    margin: 0 auto;
    border: 1px solid darkred;
    color: darkred;
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
