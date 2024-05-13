<template>
  <div class="container d-flex">
    <div class="row">
      <div class="card">
        <div class="card-head">
          <img alt="Vue logo" src="./assets/logo.png" />
        </div>
        <div class="card-body">
          <div class="form-group">
            <input
              type="text"
              class="form-control"
              placeholder="Your name"
              v-model="name"
            />
            <select
              class="form-control mt-3"
              @change="orderFruit()"
              v-model="order"
            >
              <option v-for="fruit in fruits" :key="fruit" :value="fruit">
                {{ fruit.name }}
              </option>
            </select>
            <input
              type="text"
              class="form-control mt-3"
              placeholder="Description"
              v-model="description"
            />
            <input
              type="number"
              class="form-control mt-3"
              placeholder="quantity"
              v-model="quantity"
            />
            <button @click="ordered()" type="button" class="button btn-danger mt-3">Order</button>
          </div>
        </div>
      </div>
    </div>
    <div class="card col-5">
      <div class="card-head m-3">
        <h1>Your order detail</h1>
      </div>
      <div class="card-body d-flex flex-column justify-content-start">
        <div class="row">
          <strong>Your name is: {{ name }}</strong>
        </div>
        <div class="row mt-3">
          <strong>Your order is: {{ orderName }}</strong>
        </div>
        <div class="row mt-3">
          <strong>Your detail is: {{ description }}</strong>
        </div>
        <div class="row mt-3">
          <strong>Your quantity is: {{ compareQuantity }}</strong>
        </div>
        <div class="row mt-3">
          <strong>Your total price is: {{ totalCost }} $</strong>
        </div>
      </div>
    </div>
    <div class="card" v-if="ifOdered">
      <div class="card-hea">
        <img class="img-fluid" :src="getImage" alt="" />
      </div>
      <div class="card-body">
        <div class="row mt-3">
          <strong>Your order is: {{ orderName }}</strong>
        </div>
        <div class="row mt-3">
          <strong>Your detail is: {{ description }}</strong>
        </div>
        <div class="row mt-3">
          <strong>Your quantity is: {{ compareQuantity }}</strong>
        </div>
        <div class="row mt-3">
          <strong>Your total price is: {{ totalCost }} $</strong>
        </div>
        <button @click="clear()" type="button" class="button btn-danger">Clear</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      fruits: [
        {
          id: 1,
          name: "apple",
          image:
            "https://www.buildrestfoods.com/wp-content/uploads/2020/08/green-apply.jpg",
          quantity: 10,
          description: "Apple is fresh",
          price: 10,
        },
        {
          id: 2,
          name: "banana",
          image:
            "https://www.shutterstock.com/image-photo/bunch-bananas-isolated-on-white-600nw-1722111529.jpg",
          quantity: 4,
          description: "Banana is good",
          price: 5,
        },
        {
          id: 3,
          name: "Coconut",
          image:
            "https://facts.net/wp-content/uploads/2023/09/14-facts-about-coconut-1695067813.jpg",
          quantity: 4,
          description: "Coconut is much better",
          price: 30,
        },
        {
          id: 4,
          name: "Mango",
          image:
            "https://www.kandyfreshfruits.com/wp-content/uploads/2013/06/mango1.jpg",
          quantity: 4,
          description: "Mango is much better",
          price: 15,
        },
      ],
      order: "",
      name: "",
      description: "",
      quantity: 0,
      ifOdered : false,
    };
  },
  methods: {
    orderFruit() {
      console.log(this.order.quantity);
    },
    ordered(){
      this.ifOdered = true;
    },
    clear(){
      this.ifOdered = false;
    }
  },
  computed: {
    totalCost() {
      return this.quantity * this.order.price;
    },
    orderName() {
      return this.order.name;
    },
    compareQuantity() {
      if (this.quantity < this.order.quantity) {
        return "You can order more than " + this.quantity;
      } else {
        return "You cannot order more than " + this.quantity;
      }
    },
    getImage() {
      return this.order.image;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
