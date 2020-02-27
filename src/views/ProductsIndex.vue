<template>
  <div class="products-index">
    <h1>{{ message }}</h1>
    <br />
    <h1>All Products</h1>
    <div v-for="product in products">
      <h2>{{ product.name }}</h2>
      <router-link :to="`/products/${product.id}`">More Info</router-link>
      <br />
      <img src="${product.images.url}" />
      <p>Description: {{ product.description }}</p>
      <p>Height: {{ product.price }}</p>
    </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "Welcome to The Smart People Store!",
      products: []
    };
  },
  created: function() {
    axios.get("/api/products").then(response => {
      this.products = response.data;
    });
  },
  methods: {}
};
</script>
