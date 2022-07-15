<template>
  <div id="app">
    <PhotoEditor />
  </div>
</template>

<script>
import PhotoEditor from './components/PhotoEditor'

export default {
  name: 'App',
  components: {
    PhotoEditor,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>