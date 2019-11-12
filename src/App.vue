<template>
  <div id="app">
    <header-component></header-component>
    <div class="wrapper">
      <div class="container">
        <router-view/>
      </div>
    </div>

  </div>
</template>
<script>
import headerComponent from '../src/components/header'
export default {
  name: 'app',
  data () {
    return {
      product: '',
      products: [],
      subLevel: ''
    }
  },
  components: {
    headerComponent
  }
}
</script>
<style lang="scss">
  body{
    margin: 0;
    padding: 0;
  }
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin: 0;
    background-color: #ecfcfe;
  }

  #nav {
    padding: 30px;

    a {
      font-weight: bold;
      color: #2c3e50;

      &.router-link-exact-active {
        color: #42b983;
      }
    }
  }
</style>
