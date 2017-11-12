<template>
  <transition name="slide-fade">
    <div v-if="searchResults.length" class="result-container">
      <ul>
        <li v-for="result in searchResults" v-bind:result="result">
          {{ result.title }}
          <p v-if="result.selftext.length">{{ result.selftext }}</p>
          <a v-bind:href="result.url">Read this thread...</a>
        </li>
      </ul>
    </div>
  </transition>
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
  a {
    color: mediumseagreen
  }
  p {
    color: gray;
  }
  .slide-fade-enter {
    transform: translateY(30px);
    opacity: 0;
  }
  .slide-fade-enter-active {
    transition: all .8s ease;
  }
</style>
