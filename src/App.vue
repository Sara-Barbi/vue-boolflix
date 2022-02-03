<template>
  <div id="app">
    
    <Headers />
    <Mains />
    <Footers />
  </div>
</template>

<script>
import Heladers from './components/Headers.vue'
import Mains from './components/Mains.vue'
import Footers from './components/Footers.vue'

export default {
  name: 'App',
  components: {
    Headers,
    Mains,
    Footers
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
