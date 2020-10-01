<template>
  <div id="app">
    <Search/>
    <Sort />
    <Layout :data="data" />
  </div>
</template>

<script>
import Layout from './components/Layout';
import Search from './components/Search';
import Sort from './components/Sort'

export default {
  name: 'App',
  components: {
    Layout,
    Search,
    Sort
  },
  data() {
    return {
      data: []
    }
  },
  async mounted() {
    const response = await fetch('http://localhost:3000/result');
    const result = await response.json();
    this.data = result.data;
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
    @include center($max-width, $min-width)
</style>
