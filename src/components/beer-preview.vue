<template>
  <div class="beer-table" v-if="Beer">
    <!-- v-for="item in beers" :key="item.name" -->
    <div class="beer-table__details">
      <h1>
        {{ Beer.name }}
      </h1>
      <h5>
        {{ Beer.tagline }}
      </h5>
      <h5>
        {{ Beer.first_brewed }}
      </h5>
      <button class="button hvr-sweep-to-left" @click="showModal = true">
        SEE MORE
      </button>
    </div>
    <div class="beer-table__preview">
      <img :src="Beer.image_url" :alt="Beer.name" />
    </div>
    <transition name="slide" appear>
      <div class="modal hide fade" tabindex="-1" v-if="showModal">
        <button class="close-button" @click="showModal = false">
          X
        </button>
        <div class="left-elements">
          <div class="strong-name">
            <p>{{ Beer.name }}</p>
          </div>
          <div class="modal-img">
            <img :src="Beer.image_url" :alt="Beer.name" />
          </div>
        </div>
        <div class="informations-panel">
          <ul>
            <h1>{{ Beer.name }}</h1>
            <h4>{{ Beer.tagline }}</h4>
            <p>{{ Beer.description }}</p>
          </ul>
          <div class="title-informations">SPECIFICATIONS</div>
          <table class="specifications">
            <thead>
              <tr>
                <th class="text-left" scope="col">First brewed</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>{{ Beer.first_brewed }}</td>
              </tr>
            </tbody>
          </table>
          <table class="specifications">
            <thead>
              <tr>
                <th class="text-left" scope="col">ABV</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>{{ Beer.abv }}</td>
              </tr>
            </tbody>
          </table>
          <table class="specifications">
            <thead>
              <tr>
                <th class="text-left" scope="col">IBU</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>{{ Beer.ibu }}</td>
              </tr>
            </tbody>
          </table>
          <table class="specifications">
            <thead>
              <tr>
                <th class="text-left" scope="col">EBC / SRM</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>{{ Beer.ebc }} / {{ Beer.srm }}</td>
              </tr>
            </tbody>
          </table>
          <div class="title-informations">INGREDIENTS</div>
          <table class="ingredients">
            <thead>
              <tr>
                <th class="text-left" scope="col">MALT</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td v-for="item in Beer.ingredients.malt" :key="item.name">
                  {{ item.name }}
                </td>
              </tr>
            </tbody>
          </table>
          <table class="ingredients">
            <thead>
              <tr>
                <th class="text-left" scope="col">YEAST</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>{{ Beer.ingredients.yeast }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: "BeerPreview",

  methods: {
    show() {
      this.$modal.show("hello-world");
    },
    hide() {
      this.$modal.hide("hello-world");
    },
  },

  mounted() {
    this.$modal.show("hello-world");
  },

  data: function() {
    return {
      beers: [],
      showModal: false,
    };
  },
  created: async function() {
    try {
      var response = await fetch(
        "https://api.punkapi.com/v2/beers?page=1&per_page=60"
      );
      var data = await response.json();
      this.beers = data;
    } catch (error) {
      console.log(error);
    }
  },
  computed: {
    Beer: function() {
      return this.beers[54];
    },
  },
};
</script>

<style scoped>
.beer-table {
  position: absolute;
  top: 20%;
  left: 15%;
  display: grid;
  grid-template-columns: 1fr 1fr;
  margin-block-start: 0em;
  margin-block-end: 0em;
}

.beer-table__preview {
  transform: scale(0.5, 0.5);
  justify-content: right;
  max-height: 100px;
  margin-left: 5%;
  margin-block-start: 0em;
  margin-block-end: 0em;
}

.beer-table__details {
  max-width: 300px;
  text-align: right;
  color: #000000;
  margin-block-start: 0em;
  margin-block-end: 0em;
}

.beer-table__details h1 {
  font-size: 35px;
  letter-spacing: 0;
  text-transform: uppercase;
  font-family: "Druk Wide";
  margin-block-start: 0em;
  margin-block-end: 0.3em;
}

.beer-table__details h5 {
  font-size: 20px;
  letter-spacing: 0;
  text-transform: uppercase;
  font-family: "Helvetica";
  margin-block-start: 0em;
  margin-block-end: 0.5em;
}

.close-button {
  appearance: none;
  outline: none;
  border: none;
  background: none;
  cursor: pointer;
  display: inline-block;
  font-size: 50px;
  margin-top: 200px;
  z-index: 6;
}

.button {
  appearance: none;
  outline: none;
  border: none;
  background: none;
  cursor: pointer;
  display: inline-block;
  width: 180px;
  height: 49px;
  background-color: #000000;
  color: white;
  font-family: "Helvetica";
  font-weight: 550;
  transition: color 0.5s ease;
  font-size: 14px;
}

.button:hover {
  color: #ffd512;
}

.hvr-sweep-to-left {
  display: inline-block;
  vertical-align: middle;
  -webkit-transform: translateZ(0);
  transform: translateZ(0);
  box-shadow: 0 0 1px rgba(0, 0, 0, 0);
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  -moz-osx-font-smoothing: grayscale;
  position: relative;
  -webkit-transition-property: color;
  transition-property: color;
  -webkit-transition-duration: 0.3s;
  transition-duration: 0.3s;
}
.hvr-sweep-to-left:before {
  content: "";
  position: absolute;
  z-index: -1;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: #ffcf00;
  -webkit-transform: scaleX(0);
  transform: scaleX(0);
  -webkit-transform-origin: 100% 50%;
  transform-origin: 100% 50%;
  -webkit-transition-property: transform;
  transition-property: transform;
  -webkit-transition-duration: 0.3s;
  transition-duration: 0.3s;
  -webkit-transition-timing-function: ease-out;
  transition-timing-function: ease-out;
}
.hvr-sweep-to-left:hover,
.hvr-sweep-to-left:focus,
.hvr-sweep-to-left:active {
  color: black;
}
.hvr-sweep-to-left:hover:before,
.hvr-sweep-to-left:focus:before,
.hvr-sweep-to-left:active:before {
  -webkit-transform: scaleX(1);
  transform: scaleX(1);
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 3;
  width: 100%;
  height: 100%;
  max-width: 4000px;
  max-height: 4000px;
  background-color: #fff;
  overflow-y: auto;
}

.left-elements {
  position: absolute;
  left: 10%;
  border-right: 2px solid;
  color: #d8d8d8;
  width: 40%;
}

.strong-name {
  position: absolute;
  left: 0%;
  top: 5%;
  max-width: 300px;
  text-align: center;
  font-family: "Druk Wide";
  font-size: 100px;
  color: #ffd512;
  line-height: 40px;
}

.modal-img {
  position: relative;
  top: 0%;
  left: 0%;
  top: -320px;
  transform: scale(0.6, 0.6);
  align-self: center;
}

.informations-panel {
  position: absolute;
  display: grid;
  position: fixed;
  top: 25%;
  left: 60%;
  max-width: 500px;
}

.informations-panel h1 {
  font-family: "Druk Wide";
  text-align: left;
  font-size: 45px;
  color: #000000;
  text-transform: uppercase;
  line-height: 60px;
  margin: auto;
  margin-block-start: 0em;
  margin-block-end: 0.3em;
}

.informations-panel h4 {
  font-family: "Helvetica";
  text-align: left;
  margin: auto;
  font-size: 20px;
  line-height: 30px;
  color: #000000;
  margin-block-start: 0em;
  margin-block-end: 0em;
}

.informations-panel p {
  text-align: left;
  color: #000000;
  font-family: "Helvetica";
  line-height: 22px;
  font-size: 14px;
}

.title-informations {
  text-align: left;
  color: #cccccc;
  font-family: "Helvetica";
  font-size: 20px;
  margin-block-start: 0em;
  margin-block-end: 1em;
  font-weight: 550;
}

.informations-panel th {
  text-align: left;
  color: #000000;
  font-family: "Helvetica";
  font-size: 14px;
}

.informations-panel td {
  text-align: right;
  color: #000000;
  font-family: "Helvetica";
  font-size: 14px;
}

table {
  border-block-start: 1px solid #d8d8d8;
  background-color: #fff;
  padding: 10px;
}
</style>
