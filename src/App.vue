<template>
  <div id="app">
    <Search/>
    <Sort />
    <Layout />
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
  mounted() {
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
