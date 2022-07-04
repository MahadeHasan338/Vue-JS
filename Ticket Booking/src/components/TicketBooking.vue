<template>
     <div id="app">
      <h1 class="app-title">Ticket Booking App</h1>
      <div class="ticket-app">
        <div class="confirmed-dialog" v-if="confirmed">
          <h3>Ticket confirmed!</h3>
          <hr />
          <br />
          <table class="selected-seats">
            <tr>
              <th>Passenger Name</th>
              <td>{{name}}</td>
            </tr>

            <tr>
              <th>Passenger Contact</th>
              <td>{{mobile}}</td>
            </tr>
            <tr>
              <th>Seats:</th>
              <td>
                <div v-for="(seat) in selectedSeats" :key="seat.name">
                  <div>{{seat.name}}</div>
                </div>
              </td>
            </tr>
            <tr>
              <th>Total Cost</th>
              <td>Tk. {{totalCost}}</td>
            </tr>
          </table>

          <br />

          <button class="confirm-button" @click="resetData">Book Again</button>
        </div>
        <div class="ticket-app__top">
          <div class="seat-states">
            <div class="seat-state" v-for="(value, index) in seatStates" :key="index">
              <div
                class="seat-state__color"
                :style="{backgroundColor: value.color}"
              ></div>
              <div class="seat-state__text">{{ value.text }}</div>
            </div>
          </div>
        </div>
        <div class="ticket-app__bottom">
          <div class="ticket-app__left">
            <div class="bus">
              <div class="bus__top">
                <div class="bus__door">Door</div>
                <div class="bus__driver">Driver</div>
              </div>

              <div class="seats">
                <div
                  class="seat"
                  :class="{
                    'seat--sold': seat.type === 'sold',
                    'seat--booked': seat.type === 'booked',
                    'seat--selected': seat.type === 'selected'
                    
                  }"
                  v-for="(seat, i) in seats"
                  :key="seat.name"
                  @click="handleClick(i)"
                >
                  {{seat.name}}
                </div>
              </div>
            </div>
          </div>

          <div
            class="ticket-app__instruction"
            v-if="selectedSeats.length === 0"
          >
            No seats selected <br />
            Select some seats first
          </div>

          <div class="ticket-app__right" v-else>
            <div class="cart">
              <strong>Selected Seats</strong>
              <table class="selected-seats">
                <thead>
                  <tr>
                    <th>Seat</th>
                    <th>Price</th>
                  </tr>
                </thead>
                <tbody>
                  <tr v-for="(seat) in selectedSeats" :key="seat.name">
                    <td>{{seat.name}}</td>
                    <td>Tk. {{seat.price}}</td>
                  </tr>

                  <tr v-if="appliedCoupon !== null">
                    <th>Discount</th>
                    <th>Tk. -{{appliedCoupon.discount}}</th>
                  </tr>

                  <tr>
                    <th>Total</th>
                    <th>Tk. {{totalCost}}</th>
                  </tr>
                </tbody>
              </table>

              <p v-if="appliedCoupon === null">
                Have a coupon?
                <input
                  type="text"
                  v-model="couponCode"
                  placeholder="10 Digits Code"
                />
              </p>

              <p v-else>Applied Coupon : {{ appliedCoupon.code }}</p>
            </div>

            <div class="info">
              <input type="text" placeholder="Name" v-model="name" />
              <input type="text" placeholder="Mobile" v-model="mobile" />
            </div>

            <button class="confirm-button" @click="confirm">Confirm</button>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      confirmed: false,
      name: "",
      mobile: "",
      appliedCoupon: null,
      couponCode: "",
      coupons: [
        {
          code: "100TAKAOFF",
          discount: 100
        },
        {
          code: "200TAKAOFF",
          discount: 200
        }
      ],
      seatStates: {
        sold: {
          text: "Sold",
          color: "#ff0000"
        },
        available: {
          text: "Available",
          color: "#fff"
        },
        booked: {
          text: "Booked",
          color: "gray"
        },
        selected: {
          text: "Selected",
          color: "#00ff00"
        }
      },

      seats: [
        {
          name: "A1",
          type: "available",
          price: 500
        },
        {
          name: "A2",
          type: "available",
          price: 500
        },
        {
          name: "A3",
          type: "available",
          price: 500
        },
        {
          name: "A4",
          type: "available",
          price: 500
        },
        {
          name: "B1",
          type: "available",
          price: 450
        },
        {
          name: "B2",
          type: "available",
          price: 450
        },
        {
          name: "B3",
          type: "available",
          price: 450
        },
        {
          name: "B4",
          type: "available",
          price: 450
        },
        {
          name: "C1",
          type: "sold",
          price: 500
        },
        {
          name: "C2",
          type: "sold",
          price: 500
        },
        {
          name: "C3",
          type: "sold",
          price: 500
        },
        {
          name: "C4",
          type: "sold",
          price: 500
        },
        {
          name: "D1",
          type: "available",
          price: 400
        },
        {
          name: "D2",
          type: "available",
          price: 400
        },
        {
          name: "D3",
          type: "available",
          price: 400
        },
        {
          name: "D4",
          type: "available",
          price: 400
        },
        {
          name: "E1",
          type: "available",
          price: 300
        },
        {
          name: "E2",
          type: "available",
          price: 300
        },
        {
          name: "E3",
          type: "booked",
          price: 300
        },
        {
          name: "E4",
          type: "booked",
          price: 300
        },
        {
          name: "F1",
          type: "available",
          price: 300
        },
        {
          name: "F2",
          type: "available",
          price: 300
        },
        {
          name: "F3",
          type: "available",
          price: 300
        },
        {
          name: "F4",
          type: "available",
          price: 300
        }
      ]
    };
  },

  computed: {
    selectedSeats() {
      let sc = this.seats.filter((item) => item.type === "selected");
      return sc;
    },
    totalCost() {
      let tc = 0;
      this.selectedSeats.forEach((seat) => {
        tc += seat.price;
      });

      if (this.appliedCoupon !== null) {
        tc = tc - this.appliedCoupon.discount;
      }

      return tc;
    }
  },

  methods: {
    handleClick(i) {
      let clickedSeat = this.seats[i];
      if (clickedSeat.type === "sold" || clickedSeat.type === "booked") {
        alert("You can not select this seat");
        return;
      }

      if (clickedSeat.type == "available" && this.selectedSeats.length > 2) {
        alert("You can not select more than 3 seats");
        return;
      }

      clickedSeat.type =
        clickedSeat.type === "selected" ? "available" : "selected";

      console.log(clickedSeat);
    },

    confirm() {
      if (!this.name || !this.mobile) {
        alert("Please enter name and mobile");
        return;
      }

      this.confirmed = true;
    },

    resetData() {
      this.confirmed = false;
      this.name = "";
      this.mobile = "";
      this.appliedCoupon = null;

      this.seats.forEach((seat) => {
        if (seat.type === "selected") {
          seat.type = "sold";
        }
      });
    }
  },

  watch: {
    couponCode(newValue) {
      if (newValue.length === 10) {
        let searchedCoupons = this.coupons.filter(
          (item) => item.code === newValue
        );

        if (searchedCoupons.length === 1) {
          this.appliedCoupon = searchedCoupons[0];
          this.couponCode = "";
        } else {
          alert("Coupon not valid!");
        }
      }
    }
  },
}
</script>