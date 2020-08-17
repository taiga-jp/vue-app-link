<template>
  <div id="app">
    <Header></Header>
    <ConversionLink></ConversionLink>
    <CopyText></CopyText>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import ConversionLink from './components/ConversionLink.vue'
import CopyText from './components/CopyText.vue'

export default {
  name: 'App',
  components: {
    Header,
    ConversionLink,
    CopyText
  }
}
</script>

<style>
body {
  background: #efefef;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 960px;
  margin: 160px auto 0;
  padding: 30px 10px;
  color: #2c3e50;
  background-color: #fff;
  border-radius: 4px;
  box-shadow: 0 3px 6px rgba(0,0,0,.2);
}
</style>
