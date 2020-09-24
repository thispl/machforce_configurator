<template>
  <div id="app">
    <Order />
  </div>
</template>

<script>
// import Configurator from './components/Configurator.vue'
import Order from './components/Order.vue'

export default {
  components: {
    // Configurator, 
    Order
  },
  data() {
    return {
      showConfig: true
    }
  }
}
</script>

<style lang="scss">
  body {
    margin: 0;
    padding: 0;
  }
</style>
