<template>
  <ScrollAnimation />
</template>

<script>
import ScrollAnimation from "./components/ScrollAnimation.vue";
export default {
  components: { ScrollAnimation },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");

* {
  box-sizing: border-box;
}

body {
  background-color: #efedd6;
  font-family: "Roboto", sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin: 0;
  overflow-x: hidden;
}
</style>
