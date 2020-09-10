<template>
  <header class='head'>
    <div class='b-button'>
      <span><a href='/'>B</a></span>
    </div>
    <div class='beer-button'>
      <span><a href='/'>🍺</a></span>
    </div>
  </header>
</template>

<script>
export default {
  name: 'NavBar'
};
</script>

<!-- Add 'scoped' attribute to limit CSS to this component only -->
<style scoped>
a { 
  color: #000000;
  text-decoration: none;
}

a:hover {
  color: #202020;
  text-decoration: none;
  cursor: pointer;
}
.head {
  z-index: 5;
  position: fixed;
    display: flex;
  flex-wrap: wrap;
  top: 0%;
  border-bottom: 2px solid #d8d8d8;
  background-color: #ffffff;
  font-family: 'Druk Wide';
  height: 80px;
  width: 100%;
}
.b-button {
  position: absolute;
  margin: auto;
  top: 20%;
  left: 5%;
  color: #000000;
  font-family: 'Druk Wide';
  font-size: 40px;
}
.beer-button {
  position: absolute;
  margin: auto;
  top: 20%;
  right: 5%;
  color: #000000;
  font-family: 'Apple Color Emoji';
  font-size: 40px;
}
</style>
