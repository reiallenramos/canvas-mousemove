<template>
  <div id="app">
    <h1>Drawing with mousemove event</h1>
    <canvas id="myCanvas" width="560" height="360" @mousemove="draw" @mousedown="beginDrawing" @mouseup="stopDrawing" />
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
      canvas: null,
      isDrawing: false,
      x: 0,
      y: 0,
    }
  },
  methods: {
    showCoordinates(e) {
      this.x = e.offsetX;
      this.y = e.offsetY;
    },
    drawLine(x1, y1, x2, y2) {
      let ctx = this.canvas;
      ctx.beginPath();
      ctx.strokeStyle = 'black';
      ctx.lineWidth = 1;
      ctx.moveTo(x1, y1);
      ctx.lineTo(x2, y2);
      ctx.stroke();
      ctx.closePath();
    },
    draw(e) {
      if(this.isDrawing) {
        this.drawLine(this.x, this.y, e.offsetX, e.offsetY);
        this.x = e.offsetX;
        this.y = e.offsetY;
      }
    },
    beginDrawing(e) {
      this.x = e.offsetX;
      this.y = e.offsetY;
      this.isDrawing = true;
    },
    stopDrawing(e) {
      if (this.isDrawing) {
        this.drawLine(this.x, this.y, e.offsetX, e.offsetY);
        this.x = 0;
        this.y = 0;
        this.isDrawing = false;
      }
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
