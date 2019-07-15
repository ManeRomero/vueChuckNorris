<template>
  <div class="">
    <h4>{{ frase }}</h4>
    <img alt="Chuck Norris es el Hombre." 
    src="http://cinedivergente.com/wp-content/uploads/2015/08/Chuck-Norris-vs-Communism.jpg">
    <chucknorris titulo="chuck norris ahora usa Vue!" fraseChuck="getFrase()"/>

  </div>
</template>

<script>
import chucknorris from "@/components/chucknorris.vue";

export default {
  name: "home",
  data() {
    return {
      frase: ""
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
      let result = "";
      fetch("https://api.chucknorris.io/jokes/random").then(resp => {
        resp.json().then(function(data) {
          console.log(data.value);
          this.frase = data.value;
        });
      });
    }
  }
};
</script>
