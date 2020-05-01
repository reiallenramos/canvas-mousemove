<template>
  <div id="app">
    <h1>Drawing with mousemove event</h1>
    <canvas id="myCanvas" width="560" height="360" />
  </div>
</template>

<style>
#myCanvas {
  border: 1px solid grey;
}
</style>

<script>
export default {
  data() {
    return {
      canvas: null
    }
  },
  mounted() {
    var c = document.getElementById("myCanvas");
    this.canvas = c.getContext('2d');
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
