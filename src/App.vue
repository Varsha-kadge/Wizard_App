<template>
  <Wizard/>
</template>

<script>
import Wizard from './components/Wizard.vue';
export default {
  name: 'App',
  components: {
    Wizard
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
@import "../public/custom.scss";
</style>
