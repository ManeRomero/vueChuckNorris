<template>
  <div>
    <chucknorris 
      titulo="chuck norris ahora usa Vue!"
      :fraseChuck="frase"
      :imgPath="imgPath" 
      :imgAlt="imgAlt"
    />
  </div>
</template>

<script>
import chucknorris from "@/components/chucknorris.vue";

export default {
  data() {
    return {
      frase: "",
      imgPath:
        "http://cinedivergente.com/wp-content/uploads/2015/08/Chuck-Norris-vs-Communism.jpg",
      imgAlt: "Chuck Norris puede vencer hasta con el Comunismo"
    };
  },
  mounted() {
    this.getFrase();
  },
  components: {
    chucknorris
  },
  methods: {
    async getFrase() {
      let resp = await fetch("https://api.chucknorris.io/jokes/random");
      let data = await resp.json();
      this.frase = data.value.toUpperCase();
    }
  }
};
</script>
