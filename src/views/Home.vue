<template>
  <div>
    <chucknorris titulo="chuck norris ahora usa Vue!"
      :frase="frase"
      :imgPath="imgPath" 
      :imgAlt="imgAlt"/>
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
      imgAlt: "Chuck Norris haría que el Comunismo funcionase"
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
      this.translateFrase();
    },

    async translateFrase() {
      if (this.frase.length === 0) {
        return "...relájate o sufre la ira de Chuck!";
      } else {
        let arrUrls = [
          "https://translate.yandex.net",
          "/api/v1.5/tr.json/translate?lang=en-es&key=",
          "trnsl.1.1.20190716T202405Z.18540fd6fcd25f09.4c8a21645fc436d7b42a51a1b4c62ddb0abf947e",
          "&text="
        ];

        let fraseTraducir = this.frase.split(" ").join("+");
        arrUrls.push(fraseTraducir);
        let urlToQuery = arrUrls.join("");

        let resp = await fetch(urlToQuery);
        let data = await resp.json();

        return (this.frase = data.text[0]);
      }
    }
  }
};
</script>
