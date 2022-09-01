<template>
  <div>
    <div class="container">
      <div class="row mt-4">
        <div class="col">
          <h1>Food <strong>List </strong></h1>
        </div>
      </div>

      <div class="row mt-3">
        <div class="col">
          <div class="input-group mb-3">
            <input
              v-model="search"
              type="text"
              class="form-control"
              placeholder="find your favorite food"
              aria-label="Cari"
              aria-describedby="basic-addon1"
              @keyup="searchItem"
            />
            <div class="input-group-prepend">
              <span class="input-group-text" id="basic-addon1">
                <b-icon-search></b-icon-search>
              </span>
            </div>
          </div>
        </div>
      </div>

      <div class="row mb-4">
        <div
          class="col-md-4 mt-4"
          v-for="product in products"
          :key="product.id"
        >
          <CardProduct :product="product" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CardProduct from "@/components/CardProduct.vue";
import axios from "axios";

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Foods',
    components: {
      CardProduct
    },
  data() {
    return {
      products : [],
      search : ''
    }
  },
  methods: {
    setProducts(data){
      this.products = data;
    },
    // methods search item
    searchItem(){
      axios.get('http://localhost:3000/products?q='+this.search)
      .then((response) => this.setProducts(response.data))
      .catch((error) => console.log(error))
    }
  },
  mounted() {
    axios.get('http://localhost:3000/products')
    .then((response) => this.setProducts(response.data))
      .catch((error) => console.log(error))
  },

}
</script>

<style>
</style>