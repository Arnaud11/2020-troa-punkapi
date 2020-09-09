<template>
  <footer>
    <div class='container'>
      <div class='cheers'>
        <p>CHEERS</p>
      </div>
      <div class='credit'>
        <p>PUNK API V2</p>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer'
};
</script>

<!-- Add 'scoped' attribute to limit CSS to this component only -->
<style scoped>
.container {
  z-index: 100;
  position: fixed;
  margin-bottom: 2%;
  bottom: 0%;
  border-bottom: 2px solid #d8d8d8;
  border-top: 2px solid #d8d8d8;
  background-color: #ffffff;
  font-family: 'Druk Wide';
  height: 100px;
  width: 100%;
}

.cheers {
  position: absolute;
  color: black;
  margin: auto;
  top: 30%;
  left: 5%;
}

.credit {
  position: absolute;
  margin: auto;
  color: black;
  top: 30%;
  right: 5%;
}
</style>
