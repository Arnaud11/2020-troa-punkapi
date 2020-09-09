<template>
  <div class='beers'>
    <h1>BEERS</h1>
  </div>
</template>

<script>
export default {
  name: 'Beers'
};
</script>

<!-- Add 'scoped' attribute to limit CSS to this component only -->
<style scoped>
.beers {
  position: relative;
  z-index: -1;
  height: 100%;
  width: 100%;
  transform: rotate(90deg);
  color: #ffcf00;
  font-family: 'Druk Wide';
  font-size: 350px;
  letter-spacing: 0;
  line-height: 1000px;
}
</style>
