<template>
  <div id="app">
   <Layout />
  </div>
</template>

<script>
import Layout from './components/Layout'

export default {
  name: 'App',
  components: {
    Layout
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
    @include loadFont
  #app
</style>
