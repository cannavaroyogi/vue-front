<template>
  <div class="home">
    <AppNavbar />
    <div class="container">
      <AppHero />
      <div class="row mt-2">
        <div class="col">
          <h2><strong> Best </strong> Comics</h2>
        </div>
        <div class="col">
          <router-link to="/comics" class="btn btn-danger float-right"
            ><b-icon-eye></b-icon-eye> Lihat semua
          </router-link>
        </div>
      </div>
      <div class="row mb-4">
        <!-- Rumus menghitung kolom bootsrap 12/nilai md misal nilai md-3 berarti 12/3 = 4, 
        jadi ada 4 kolom yang bisa di render dalam 1 baris 
        v-for untuk foreach di vue-->
        <div class="col-md-4 mt-4 mb-4" v-for="product in products" :key="product.id">
          <CardProduct :product=  "product"/>
        </div>
      </div>
    </div>
    <AppFooter />
  </div>
</template>

<script>
// @ is an alias to /src
import AppNavbar from "@/components/AppNavbar.vue";
import AppHero from "@/components/AppHero.vue";
import CardProduct from "@/components/CardProduct.vue";
import AppFooter from "@/components/AppFooter.vue";
import axios from 'axios';

export default {
  name: "HomeView",
  components: {
    AppNavbar,
    AppHero,
    CardProduct,
    AppFooter
  },
  data() {
    return {
      products: []
    }
  },
  methods: {
    setProduct(data) {
      this.products = data
    }
  },
  mounted() {
    axios.get('http://127.0.0.1/products')
    .then((response) => {
      //console.log("Success: ",response.data.data);
      this.setProduct(response.data.data);
    }).catch ((err) =>{
      console.log(err)
    });
  }
};
</script>
