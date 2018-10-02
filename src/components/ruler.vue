<template lang="html">
  <canvas canvas-id="canvas" :style="{width: canvasWidth + 'px', height: canvasHeight+'px'}"></canvas>
</template>

<script>
export default {
  data() {
    return {
      canvasWidth: 0,
      canvasHeight: 0,
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
      let lineSum = 100;

      for (let i = 0; i < lineSum; i++) {
        let startPos = {
          x: 0,
          y: parseInt(10 + i * 3.7) + 0.5
        };
        let len = 0;
        if (i === 0 ) {
          len = 30;
          this.drawText(ctx, i, {x: len + 10, y: 14 + i * 4});
        }
        else if (i % 10 === 9) {
          len = 30;
          this.drawText(ctx, (i+1)/10, {x: len + 10, y: 14 + i * 3.7});
        }
        else if (i % 10 === 4) {
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
