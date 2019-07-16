<template>
  <div class="">
    <h4>{{ frase }}</h4>
    <img alt="Chuck Norris es el Hombre." 
    src="http://cinedivergente.com/wp-content/uploads/2015/08/Chuck-Norris-vs-Communism.jpg">
    <chucknorris titulo="chuck norris ahora usa Vue!" :fraseChuck="frase"/>

  </div>
</template>

<script>
import chucknorris from "@/components/chucknorris.vue";

export default {
  name: "home",
  data() {
    return {
      frase: "dddddd"
    };
  },
  mounted() {
    this.getFrase();
  },
  components: {
    chucknorris
  },
  methods: {
    getFrase() {
      fetch("https://api.chucknorris.io/jokes/random").then(resp => {
        resp.json().then((data) => {
          this.frase = data.value;
        });
      });
    }
  }
};
</script>
