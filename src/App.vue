<template>
    <ProductList />
</template>

<script>
import ProductList from './components/ProductList'

export default {
  name: 'App',
  components: {
    ProductList,
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