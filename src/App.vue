<template>
  <div id="app">
    <Test />
    <!-- <Configurator /> -->
  </div>
</template>

<script>
// import Configurator from './components/Configurator.vue'
import Test from './components/Test.vue'

export default {
  components: {
    // Configurator
    Test
  }
}
</script>

<style lang="scss">
  body {
    margin: 0;
    padding: 0;
  }
</style>
