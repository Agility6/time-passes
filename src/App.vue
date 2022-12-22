<template>
  <div id="app">
    <Time />
  </div>
</template>

<script>
import Time from './components/Time.vue'

export default {
  name: 'App',
  components: {
    Time
  }
}
</script>

<style lang="scss">
*{
  padding: 0;
  margin: 0;
}
#app {
  width: 100%;
  height: 100vh;
  overflow: hidden;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #023059;
  background-color: #011526;
}
</style>
