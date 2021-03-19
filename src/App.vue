<template>
  <div id="app">
    <Skills />
  </div>
</template>

<script>
import Skills from "./components/Skills.vue";

export default {
  name: "App",
  components: {
    Skills,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Anton&family=Big+Shoulders+Stencil+Text:wght@300&family=Goldman:wght@700&family=PT+Sans&display=swap");

body {
  background-color: #d3dce0;
  font-family: "Anton", sans-serif;
  font-family: "Big Shoulders Stencil Text", cursive;
  font-family: "Goldman", cursive;
  font-family: "PT Sans", sans-serif;
  display: grid;
  grid-template-rows: auto;
  justify-items: center;
  align-items: center;
}

body,
html {
  margin: 0;
  height: 100%;
}
#app {
  width: 50%;
}
</style>
