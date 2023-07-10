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
      <div v-if="load" class="row mb-4">
        <div class="col text-center">
          <div class="spinner-grow text-primary" role="status">
            <span class="sr-only">Loading...</span>
          </div>
          <div class="spinner-grow text-secondary" role="status">
            <span class="sr-only">Loading...</span>
          </div>
          <div class="spinner-grow text-success" role="status">
            <span class="sr-only">Loading...</span>
          </div>
          <div class="spinner-grow text-danger" role="status">
            <span class="sr-only">Loading...</span>
          </div>
          <div class="spinner-grow text-warning" role="status">
            <span class="sr-only">Loading...</span>
          </div>
          <div class="spinner-grow text-info" role="status">
            <span class="sr-only">Loading...</span>
          </div>
          <div class="spinner-grow text-dark" role="status">
            <span class="sr-only">Loading...</span>
          </div>
          </div>
      </div>
      <div class="row mb-4">
        <!-- Rumus menghitung kolom bootsrap 12/nilai md misal nilai md-3 berarti 12/3 = 4, 
        jadi ada 4 kolom yang bisa di render dalam 1 baris 
        v-for untuk foreach di vue-->
        <div class="col-md-4 mt-4 mb-4" v-for="product in products" :key="product.id">
          <CardProduct :product=  "product" :modalId="modalId"/>
        </div>
      </div>
    </div>
    <div class="modal-detail" v-for="product in products" :key="product.id">
      <ModalDetail :product="product" :modalId="modalId"/>
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
import ModalDetail from "@/components/ModalDetail.vue";
import axios from 'axios';

export default {
  name: "HomeView",
  components: {
    AppNavbar,
    AppHero,
    CardProduct,
    AppFooter,
    ModalDetail
  },
  data() {
    return {
      products: [],
      bestproducts: [],
      load: true,
      modalId: 'modalId',
      showModal: false // Add this line
    }
  },
  methods: {
    openModal() {
      this.showModal = true;
    },
    closeModal() {
      this.showModal = false;
    },
    setProduct(data) {
      this.products = data
    },
    setBestProduct(data) {
      this.bestproducts = data
    }
  },
  mounted() {
    axios.get('http://192.168.130.215/bestproducts')
    .then((response) => {
      //console.log("Success: ",response.data.data);
      this.setProduct(response.data.data);
      this.load = false;
    }).catch ((err) =>{
      console.log(err)
    });

    axios.get('http:/192.168.130.215/bestproducts')
    .then((response) => {
      console.log("Success: ",response.data.data);
      this.setBestProduct(response.data.data);
    }).catch ((err) =>{
      console.log(err)
    });

  }
};
</script>
