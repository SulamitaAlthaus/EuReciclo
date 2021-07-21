<template>
  <div id="app">
    <Payment/>
  </div>
</template>

<script>
import Payment from './views/Payment.vue'

export default {
  name: 'App',
  components: {
    Payment
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
  margin: -8px;
  overflow: hidden;
}
</style>
