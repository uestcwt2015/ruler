<template lang="html">
  <div class="calc-container" id="container">
    <ruler />
  </div>
</template>

<script>
import ruler from '@/components/ruler.vue';
export default {
  components: {
    ruler
  },
  mounted() {

  }
}
</script>

<style scoped>
.calc-container {
  width: 100%;
  height: 100vh;
}
</style>
