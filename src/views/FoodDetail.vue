<template>
  <div class="food-detail">
    <div class="container">
      <!-- breadcrumb -->
      <div class="row mt-5">
        <div class="col">
          <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
              <li class="breadcrumb-item">
                <router-link class="text-dart" to="/">Home</router-link>
              </li>
              <li class="breadcrumb-item">
                <router-link class="text-dart" to="/foods">Foods</router-link>
              </li>
              <li class="breadcrumb-item active" aria-current="page">
                Food Order
              </li>
            </ol>
          </nav>
        </div>
      </div>
      <!-- end breadcrumb -->
      <div class="row mt-3">
        <div class="col-md-6">
          <img
            :src="'../assets/images/' + product.gambar"
            class="img-fluid shadow"
          />
        </div>
        <div class="col-md-6">
          <h2>
            <strong>{{ product.nama }} </strong>
          </h2>
          <hr />
          <h4>
            Price :
            <strong>Rp. {{ product.harga }}</strong>
          </h4>
          <form class="mt-4" v-on:submit.prevent>
            <div class="form-group">
              <label for="jumlah_pesanan">Amount </label>
              <input
                type="number"
                class="form-control"
                v-model="pesan.jumlah_pemesanan"
              />
            </div>
            <div class="form-group">
              <label for="keterangan"> Description </label>
              <textarea
                class="form-control"
                placeholder="Description ext : Pedes, Nasi Setengah .."
                v-model="pesan.keterangan"
              ></textarea>
            </div>
            <button type="submit" class="btn btn-success" @click="pemesanan">
              <b-icon-cart></b-icon-cart>Order
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
    name :'FoodDetail',
    data(){
        return {
            product: {},
            pesan: {},
        }
    },
    methods: {
        setProduct(data) {
          this.product = data;
        },
        pemesanan(){
          this.pesan.products = this.product;
          if(this.pesan.jumlah_pemesanan){
            axios
              .post("http://localhost:3000/keranjangs", this.pesan)
              .then(() => {
                this.$router.push({ path: "/cart"})
                this.$toast.success("Sukses Masuk Keranjang", {
                  type: "success",
                  position: "top-right",
                  duration: 3000,
                  dismissible: true,
                });
              })
              .catch((err) => console.log(err));
          // eslint-disable-next-line no-empty
          } else  {
            this.$toast.error("Jumlah Pesanan Harus diisi", {
                  type: "error",
                  position: "top-right",
                  duration: 3000,
                  dismissible: true,
            });
          }
        },
    },
    mounted() {
        axios.get('http://localhost:3000/products/'+this.$route.params.id)
      .then((response) => this.setProduct(response.data))
      .catch((error) => console.log(error))

  
    }

}
</script>

<style>
</style>