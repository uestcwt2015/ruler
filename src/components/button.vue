<template lang="html">
  <span class="button" @tap="changeRoute">
    {{text}}
  </span>
</template>

<script>
export default {
  props: ['text', 'to'],
  methods: {
    changeRoute () {
      const url = '../' + this.to + '/main'
      console.log(url);
      wx.navigateTo({ url })
    }
  }
}
</script>

<style scoped>
.button {
  display: inline-block;
  color: #aaa;
  font-size: 14px;
  border: 1px solid #aaa;
  padding: 5px 10px;
  border-radius: 6px;
}
</style>
