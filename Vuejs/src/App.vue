<template>
  <div id="app">
    <ResumeParser />
  </div>
</template>

<script>
import ResumeParser from './components/ResumeParser.vue'

export default {
  name: 'App',
  components: {
    ResumeParser
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
