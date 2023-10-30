<template>
  <Akzhol msg="Welcome to My Vue.js App"/>
</template>

<script>
import Akzhol from './components/Akzhol.vue'

export default {
  name: 'App',
  components: {
    Akzhol
  }
}
</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif, Avenir;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
