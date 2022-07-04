<template>
  <div class="center">
    <div class="passanger">
      <h1>Passenger Lists</h1>
      <div v-for="(passanger, id) in passengers" :key="id">
        <img :src="passanger.src" alt="" />
        <p>{{ passanger.name }}</p>
        <p>Balance : {{ passanger.balance }} TK</p>

        <div>
          <button>Book Now</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      passengers: [
        {
          id: 1,
          name: "Jenifer Lee",
          balance: 1000,
          src: "https://images.pexels.com/photos/774909/pexels-photo-774909.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500",
        },
        {
          id: 2,
          name: "James Almond",
          balance: 2000,
          src: "https://images.unsplash.com/photo-1500648767791-00dcc994a43e?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MXx8bWVuJTIwcG9ydHJhaXR8ZW58MHx8MHx8&w=1000&q=80",
        },
        {
          id: 3,
          name: "John Sinha",
          balance: 1500,
          src: "https://images.unsplash.com/photo-1531427186611-ecfd6d936c79?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MTd8fHBvcnRyYWl0c3xlbnwwfHwwfHw%3D&w=1000&q=80",
        },
        {
          id: 4,
          name: "Happy watson",
          balance: 2500,
          src: "https://image1.masterfile.com/getImage/NjAwLTA2Njc1MTU5bi4wMDAwMDAwMA=AMjDzU/600-06675159n.jpg",
          mobile: "01363957598",
        },
      ],
    };
  },
};
</script>

<style scoped>
.passanger {
  display: inline-block;
  text-align: center;
  padding: 2rem;
}
.passanger img {
  max-width: 100%;
  width: 17rem;
}
.center {
  text-align: center;
}
</style>
