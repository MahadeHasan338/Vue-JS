<template>
  <div>
    <h1>Scroll to see the animation</h1>
    <div class="box"><h2>Content</h2></div>
    <div class="box"><h2>Content</h2></div>
    <div class="box"><h2>Content</h2></div>
    <div class="box"><h2>Content</h2></div>
    <div class="box"><h2>Content</h2></div>
    <div class="box"><h2>Content</h2></div>
    <div class="box"><h2>Content</h2></div>
    <div class="box"><h2>Content</h2></div>
    <div class="box"><h2>Content</h2></div>
    <div class="box"><h2>Content</h2></div>
    <div class="box"><h2>Content</h2></div>
    <div class="box"><h2>Content</h2></div>
    <div class="box"><h2>Content</h2></div>
  </div>
</template>

<script>
export default {
  mounted() {
    const boxes = this.$el.querySelectorAll(".box");
    window.addEventListener("scroll", checkBoxes);

    checkBoxes();

    function checkBoxes() {
      const triggerBottom = (window.innerHeight / 5) * 4;
      boxes.forEach((box) => {
        const boxTop = box.getBoundingClientRect().top;

        if (boxTop < triggerBottom) {
          box.classList.add("show");
        } else {
          box.classList.remove("show");
        }
      });
    }
  },
};
</script>

<style scoped>
h1 {
  margin: 10px;
}
.box {
  background-color: steelblue;
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 400px;
  height: 200px;
  margin: 10px;
  border-radius: 10px;
  box-shadow: 2px 4px 5px rgba(0, 0, 0, 0.3);
  transform: translateX(400%);
  transition: transform 0.4s ease;
}

.box:nth-of-type(even) {
  transform: translateX(-400%);
}

.box.show {
  transform: translateX(0);
}

.box h2 {
  font-size: 45px;
}
</style>
