<!-- resources/js/components/LandingPage.vue -->

<template>
    <div class="container">
      <div class="jumbotron text-center bg-primary text-white">
        <h1 class="display-4">Welcome to Our E-Commerce Site</h1>
        <p class="lead">Find the best products at unbeatable prices.</p>
        <hr class="my-4">
        <p>Explore our wide range of products now!</p>
        <a class="btn btn-success btn-lg" href="#" role="button">Shop Now</a>
      </div>
  
      <div class="row">
        <div class="col-md-4" v-for="product in products" :key="product.id">
          <div class="card mb-4 shadow-sm">
            <img :src="product.image" class="card-img-top" alt="Product Image">
            <div class="card-body">
              <h5 class="card-title">{{ product.name }}</h5>
              <p class="card-text">{{ product.description }}</p>
              <div class="d-flex justify-content-between align-items-center">
                <span class="text-muted">${{ product.price }}</span>
                <button type="button" class="btn btn-sm btn-outline-secondary">View</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        products: []
      };
    },
    mounted() {
      this.fetchProducts();
    },
    methods: {
      fetchProducts() {
        axios.get('/api/products')
          .then(response => {
            this.products = response.data;
          })
          .catch(error => {
            console.error('Error fetching products:', error);
          });
      }
    }
  }
  </script>
  
  <style scoped>
  .jumbotron {
    margin-top: 30px;
  }
  .card-img-top {
    height: 200px;
    object-fit: cover;
  }
  </style>
  