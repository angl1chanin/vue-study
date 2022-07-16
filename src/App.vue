<template>
  <div id="app">
    <div class="container">
      <UserForm />
    </div>
  </div>
</template>

<script>
import UserForm from './components/UserForm'

export default {
  name: 'App',
  components: {
    UserForm,
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