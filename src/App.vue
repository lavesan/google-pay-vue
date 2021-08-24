<template>
  <div id="app">
    <h1>
      Botão google pay
    </h1>
    <GooglePay totalPrice="100.00" />
  </div>
</template>

<script>
import GooglePay from './components/GooglePay.vue';

export default {
  name: 'App',
  components: {
    GooglePay,
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
