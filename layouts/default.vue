<template>
  <div class="container">
    <Logo/>
    <Nuxt/>
  </div>
</template>

<script>
import Logo from "../components/Logo";

export default {
  components: {
    Logo,
  }
}

</script>

<style>
  html {
    font-family: 'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
    font-size: 16px;
    word-spacing: 1px;
    -ms-text-size-adjust: 100%;
    -webkit-text-size-adjust: 100%;
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
    box-sizing: border-box;
  }

  *,
  *::before,
  *::after {
    box-sizing: border-box;
    margin: 0;
  }

  .container {
    max-width: 1400px;
    margin: 0 auto;
    padding: 20px;
  }
</style>
