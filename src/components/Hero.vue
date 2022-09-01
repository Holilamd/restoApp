<template>
  <div class="hero">
    <!-- desktop -->
    <div class="d-none d-md-block">
      <div class="row mt-2">
        <div class="col-md-6">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center">
              <h2><strong>Delicious Food</strong><br>In your Mobile</h2>
              <p>Ayo segera pilih dan pesan makanan favorit anda</p>
              <router-link class="btn btn-lg btn-success" to="/foods"><b-icon-arrow-right></b-icon-arrow-right> Order</router-link>
            </div>

          </div>
        </div>
        <div class="col-md-6">
          <img src="assets/images/hero.png" width="100%">
        </div>
      </div>
    </div>
    <!-- //Mobile -->
    <div class="d-sm-block d-md-none">
      <div class="row mt-2">
        <div class="col-md-6 mb-3">
          <img src="assets/images/hero.png" width="100%">
        </div>
        <div class="col-md-6">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center">
              <h2><strong>Delicious Food</strong><br>In your Mobile</h2>
              <p>Ayo segera pilih dan pesan makanan favorit anda</p>
              <button class="btn btn-lg btn-success"><b-icon-arrow-right></b-icon-arrow-right> Pesan</button>
            </div>

          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: "Hero"
}
</script>

<style>

</style>