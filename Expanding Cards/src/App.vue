<template>
  <ExpandCard />
</template>

<script>
import ExpandCard from "./components/ExpandCard.vue";
export default {
  components: { ExpandCard },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Muli&display=swap");

* {
  box-sizing: border-box;
}
body {
  font-family: "Muli", sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  overflow: hidden;
  margin: 0;
}
.container {
  display: flex;
  width: 90vw;
}
</style>
