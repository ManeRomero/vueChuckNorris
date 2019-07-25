<template>
  <div class="container">
    <h2>The Chuck Herald</h2>
    <small>Edición en Español</small>
    <div class="pic" :title="frase">
      <img :src="imgPath" :alt="imgAlt">
      <transition name="textin" mode="out-in">
        <h1 :style="lengthStyle"> {{ frase }} </h1>
      </transition>
    </div>
    <div>
      <button>{{'Pónmelo otra vez, Chuck'.toUpperCase()}}</button>
      <button>{{'Quiero jugar a la RuletaChuck!'.toUpperCase()}}</button>
      <small>powered by yandex translate ©</small>
    </div>
    <a href="https://github.com/ManeRomero">Mi GitHub</a>
  </div>
</template>

<script>
export default {
  name: "chucknorris",
  props: {
    titulo: String,
    frase: String,
    imgAlt: String,
    imgPath: String
  },
  data() {
    return {
      fraseTraducida: ""
    };
  },
  computed: {
    lengthStyle() {
      let style = "font-size: ";
      if (this.fraseTraducida.length <= 75 && this.fraseTraducida.length != 0) {
        style += "6vw";
      } else if (this.fraseTraducida.length <= 150) {
        style += "4vw";
      } else if (this.fraseTraducida.length > 150) {
        style += "2vw";
      }
      return style;
    }
  }
};
</script>

<style scoped>
.container {
  margin: auto;
  height: 95vh;
}

.pic {
  position: relative;
  display: flex;
  flex-direction: column;
  width: 80%;
  margin: auto;
  justify-content: center;
  overflow: hidden;
}

.pic ~ div {
  margin-top: 20px;
  display: flex;
  flex-direction: column;
  width: 40%;
  margin: auto;
}

h1 {
  color: white;
  z-index: 1000;
  position: absolute;
  justify-self: center;
  letter-spacing: 6px;
  margin: auto;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

img {
  width: 100%;
  height: auto;
  opacity: 0.6;
  text-align: justify;
  transform: scale(1.3);
}

button {
  padding: 10px;
  font-weight: 800;
  font-size: 1em;
  border: 5px solid gold;
  border-radius: 5px 3px 3px 1px;
  background-color: transparent;
  cursor: pointer;
}

small {
  border-bottom: 2px solid grey;
  padding: 5px;
}
</style>
