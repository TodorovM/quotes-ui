<template>
  <div id="app">
    <div class="container">
      <Search/>
      <Sort />
      <Layout/>
    </div>
  </div>
</template>

<script>
import Layout from './components/Layout';
import Search from './components/Search';
import Sort from './components/Sort'
import EventBus from './utils/eventBus'

export default {
  name: 'App',
  components: {
    Layout,
    Search,
    Sort
  },
  async mounted() {
    const response = await fetch('http://localhost:3000/result');
    const result = await response.json();
    EventBus.$emit('data_loaded', result.data)
  },
}
</script>

<style lang="sass">
  
  @include reset
  html, body
    background-color: $background
  #app
    @include loadFont
    color: $text-color
    @include center($max-width)
    overflow-x: auto
    .container
      min-width: 320px
</style>
