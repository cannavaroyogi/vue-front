<template>
  <div class="home">
    <SideBar />
    <AppNavbar />
    <div class="container">
      <AppHero />
      <div class="row mt-2">
        <div class="col">
          <h2><strong> Best </strong> Comics</h2>
        </div>
        <div class="col">
          <router-link to="/comics" class="btn btn-danger float-right"
            >Lihat semua</router-link>
        </div>
      </div>
      <!-- <div v-if="load" >
        <LoadingBar />
      </div> -->
      <CardShimmer v-if="showShimmer" />
      <div class="row mb-4">
        <!-- Rumus menghitung kolom bootsrap 12/nilai md misal nilai md-3 berarti 12/3 = 4, 
        jadi ada 4 kolom yang bisa di render dalam 1 baris 
        v-for untuk foreach di vue-->
        <div class="col-md-4 mt-4 mb-4" v-for="product in products" :key="product.id">
          <CardProduct v-if="!showShimmer" :product=  "product" :modalId="modalId"/>
        </div>
      </div>
    </div>
    <div class="modal-detail" v-for="product in products" :key="product.id">
      <ModalDetail :product="product" :modalId="modalId"/>
    </div>
    <div class="snack-bar" v-snackbar>
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
// import LoadingBar from "@/components/LoadingBar.vue";
import CardShimmer from "@/components/CardShimmer.vue";
import SideBar from "@/components/SideBar.vue";
import axios from 'axios';

export default {
  name: "HomeView",
  components: {
    AppNavbar,
    AppHero,
    CardProduct,
    AppFooter,
    ModalDetail,
    // LoadingBar,
    CardShimmer,
    SideBar
  },
  data() {
    return {
      products: [],
      bestproducts: [],
      load: true,
      modalId: 'modalId',
      url: "127.0.0.1",
      showModal: false,
      showShimmer: true // Add this line
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
    axios.get('http://'+this.url+'/bestproducts')
    .then((response) => {
      //console.log("Success: ",response.data.data);
      this.setProduct(response.data.data);
      setTimeout(() => {
          this.showShimmer = false;
        }, 1000);
    }).catch ((err) =>{
      console.log(err)
    });

    // axios.get('http://'+this.url+'/bestproducts')
    // .then((response) => {
    //   console.log("Success: ",response.data.data);
    //   this.setBestProduct(response.data.data);
    // }).catch ((err) =>{
    //   console.log(err)
    // });

  }
};
</script>
