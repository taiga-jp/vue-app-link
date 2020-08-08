<template>
  <div id="app">
    <ConversionLink></ConversionLink>
    <CopyText></CopyText>
  </div>
</template>

<script>
import ConversionLink from './components/ConversionLink.vue'
import CopyText from './components/CopyText.vue'

export default {
  name: 'App',
  components: {
    ConversionLink,
    CopyText
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
