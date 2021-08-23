<template>
  <div id="app">
    <!-- <HelloWorld /> -->
    <h1>
      Botão google pay:
    </h1>
    <GooglePay totalPrice="100.00" />
  </div>
</template>

<script>
// import HelloWorld from './views/HelloWorld'
import GooglePay from './components/GooglePay.vue';

export default {
  name: 'App',
  mounted() {
    const recaptchaScript = document.createElement("script");
    recaptchaScript.setAttribute("src", "https://pay.google.com/gp/p/js/pay.js");
    recaptchaScript.async = true;
    recaptchaScript.onload = this.$refs.googlePayButton.onGooglePayLoaded;
    document.head.appendChild(recaptchaScript);
  },
  components: {
    // HelloWorld,
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
