<template>
  <div class="beer-table" v-if="Beer">
    <div class="beer-table__preview">
      <img :src="Beer.image_url" :alt="Beer.name" />
    </div>
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
    <transition name="fade" appear>
      <div
        class="modal-overlay"
        v-if="showModal"
        @click="showModal = false"
      ></div>
    </transition>
    <transition name="slide" appear>
      <div class="modal" v-if="showModal">
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
            <h5>{{ Beer.description }}</h5>
          </ul>
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
    }
  },

  mounted() {
    this.$modal.show("hello-world");
  },

  data: function() {
    return {
      beers: [],
      showModal: true
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
      return this.beers[50];
    }
  }
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
  margin-block-end: 0em;
}

.beer-table__details h5 {
  font-size: 12px;
  letter-spacing: 0;
  text-transform: uppercase;
  font-family: "Helvetica";
  margin-block-start: 0em;
  margin-block-end: 0em;
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
  width: 150px;
  height: 40px;
  background-color: #000000;
  color: white;
  font-family: "Helvetica";
  transition: color 0.5s ease;
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

.modal-overlay {
  position: absolute;
  width: 100%;
  height: 100%;
  z-index: 2;
  background-color: rgb(255, 255, 255);
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
  max-width: 2000px;
  max-height: 2000px;
  background-color: #fff;
  border-radius: 16px;
  padding: 25px;
}

.left-elements {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 10px 2em;
}

.strong-name {
  position: absolute;
  left: 0%;
  top: 30%;
  max-width: 300px;
  text-align: center;
  font-family: "Druk Wide";
  font-size: 150px;
  color: #ffd512;
  align-self: center;
}

.modal-img {
  position: absolute;
  left: 10%;
  top: 5%;
  transform: scale(0.7, 0.7);
  align-self: center;
}

.informations-panel {
  position: absolute;
  display: grid;
  left: 60%;
  max-width: 400px;
}

.informations-panel h1 {
  font-family: "Druk Wide";
  text-align: left;
  font-size: 60px;
  color: #000000;
  margin-block-start: 0em;
  margin-block-end: 0em;
}

.informations-panel h4 {
  font-family: "Druk Wide";
  text-align: left;
  font-size:25px;
  color: #000000;
  margin-block-start: 0em;
  margin-block-end: 0em;
}

.informations-panel h5 {
  text-align: left;
  color: #000000;

  font-size: 15px;
}
</style>
