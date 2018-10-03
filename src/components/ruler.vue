<template lang="html">
  <canvas canvas-id="canvas" :style="{width: canvasWidth + 'px', height: canvasHeight+'px'}"></canvas>
</template>

<script>
export default {
  data() {
    return {
      canvasWidth: 360,
      canvasHeight: 400,
      canvasCtx: ''
    }
  },
  methods: {
    getDeviceSize() {
      const device = wx.getSystemInfoSync();
      this.canvasWidth = device.windowWidth;
      this.canvasHeight = device.windowHeight;
    },
    drawRuler() {
      const ctx = this.canvasCtx;
      const lineSpace = 4;
      let lineSum = 101;

      for (let i = 0; i < lineSum; i++) {
        let startPos = {
          x: 0,
          y: 10 + i * 6 * 1.075 * 0.9
        };
        let len = 0;
        if (i % 10 === 0) {
          len = 30;
          this.drawText(ctx, i/10, {x: len + 10, y: 14 + i * 6 * 1.075 * 0.9});
        }
        else if (i % 10 === 5) {
          len = 25;
        }
        else {
          len = 20;
        }

        this.drawLine(ctx, startPos, len);
      }
      ctx.draw(true);
    },
    drawLine(ctx, start, lineLen, lineWidth=1) {
      ctx.lineWidth = lineWidth;
      ctx.beginPath();
      ctx.moveTo(start.x, start.y);
      ctx.lineTo(start.x + lineLen, start.y);
      ctx.closePath();
      ctx.stroke();
    },
    drawText(ctx, text, pos, fontSize=12) {
      ctx.font = `${fontSize}px serif`;
      ctx.fillText(text, pos.x, pos.y);
    }
  },
  mounted() {
    this.getDeviceSize();
    this.canvasCtx = wx.createCanvasContext('canvas');
    this.drawRuler();
  }
}
</script>

<style lang="css">
</style>
