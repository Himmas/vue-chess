<template>
  <div id="app">
    <chess></chess>
  </div>
</template>

<script>
import chess from './components/chess'

export default {
  name: 'app',
  components: {
    chess
  }
}
</script>

<style lang="less">
  *{
    padding:0;margin: 0;
  }
#app {
  position: absolute;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
  width: 100%;
}
</style>
