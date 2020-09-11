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

  bottom: 0%;
  border-top: 2px solid #d8d8d8;
  background-color: #ffffff;
  font-family: 'Druk Wide';
  height: 80px;
  width: 80%;
  left: 10%;
}

.cheers {
  position: absolute;
  color: black;
  margin: auto;
  top: 20%;
  left: 15%;
}

.credit {
  position: absolute;
  margin: auto;
  color: black;
  top: 20%;
  right: 15%;
}
</style>
