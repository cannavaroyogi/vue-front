<template>
  <div class="comics">
    <AppNavbar />
    <div class="container">
        <div class="row mt-4">
          <div class="col">
            <h1> <strong> Daftar </strong> Komik </h1>
          </div>
        </div>
        <div class="row mb-4">
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
import AppNavbar from '@/components/AppNavbar.vue'
import CardProduct from "@/components/CardProduct.vue";
import AppFooter from "@/components/AppFooter.vue";
import axios from 'axios';

export default {
  name: 'ComicsView',
  components: {
    AppNavbar,
    CardProduct,
    AppFooter
  },
  data() {
    return {
      products: [],
      bestproducts: []
    }
  },
  methods: {
    setProduct(data) {
      this.products = data
    },
    setBestProduct(data) {
      this.bestproducts = data
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

    axios.get('http://127.0.0.1/bestproducts')
    .then((response) => {
      console.log("Success: ",response.data.data);
      this.setBestProduct(response.data.data);
    }).catch ((err) =>{
      console.log(err)
    });

  }
}
</script>