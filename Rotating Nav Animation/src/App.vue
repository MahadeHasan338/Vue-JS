<template>
  <RoatatigNavigation />
</template>

<script>
import RoatatigNavigation from "./components/RoatatigNavigation.vue";
export default {
  components: { RoatatigNavigation },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Lato&display=swap");

* {
  box-sizing: border-box;
}

body {
  font-family: "Lato", sans-serif;
  background-color: #333;
  color: #222;
  overflow-x: hidden;
  margin: 0;
}
</style>
