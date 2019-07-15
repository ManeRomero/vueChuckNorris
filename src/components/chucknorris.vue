<template>
  <div class="hello">
    <h3> {{fraseChuck}} </h3>
      <button>Pónmelo otra vez, Chuck</button>
      <small>{{ titulo }}</small>
  </div>
</template>

<script>
export default {
  name: "chucknorris",
  props: {
    titulo: String,
    fraseChuck: String
  }
};
</script>

<style scoped>
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

.hello {
  display: flex;
  flex-direction: column;
  max-height: 100vh;
  justify-content: space-around;
  width: 30%;
  margin: auto;
}
</style>
