<template>
  <div class="container" id="app">
    <!-- NavBar -->

    <NavBar />

    <!-- Content -->

    <div class="content-container">
      <BeerPreview />
    </div>
    <Beers />
    <router-view />

    <!-- Footer -->
    <Footer />
  </div>
</template>

<script>
import NavBar from "./components/nav-bar.vue";
import Footer from "./components/footer.vue";
import Beers from "./components/Beers.vue";
import BeerPreview from "./components/beer-preview.vue";

export default {
  name: "App",
  components: {
    NavBar,
    Beers,
    Footer,
    BeerPreview,
  },
    
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

@font-face {
  font-family: "Druk Wide";
  src: local("Druk Wide"),
    url(./fonts/@font-face/2206d6cc490084998d531e8c1b2cbb4a.ttf)
      format("truetype");
}

@font-face {
  font-family: "Helvetica";
  src: local("Helvetica"),
    url(./fonts/@font-face/FontsFree-Net-HelveticaNeueBold.ttf)
      format("truetype");
}
</style>
