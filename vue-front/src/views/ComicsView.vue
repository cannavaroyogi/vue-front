<template>
  <div class="comics">
    <AppNavbar />
    <div class="container">
        <div class="row mt-4">
          <div class="col">
            <h1> <strong> Daftar </strong> Komik </h1>
          </div>
        </div>
        <div class="row mt-4">
          <div class="col">
              <div class="input-group">
                <!-- Mendaftarkan search pada data return -->
                <input v-model="search" @keyup="searchProduct" type="text" class="form-control" placeholder="Search komik yang pengen dikoleksi" aria-label="Search Komikmu !!!">
                <div class="input-group-append">
                  <span class="btn-lg btn-danger"><b-icon-search ></b-icon-search></span>
                </div>
              </div>
          </div>
        </div>
        <div class="row mb-4">
          <div class="col-md-4 mt-4 mb-4" v-for="product in products" :key="product.id">
            <CardProduct :product=  "product"/>
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
import AppNavbar from '@/components/AppNavbar.vue'
import CardProduct from "@/components/CardProduct.vue";
import AppFooter from "@/components/AppFooter.vue";
import ModalDetail from "@/components/ModalDetail.vue";
import axios from 'axios';

export default {
  name: 'ComicsView',
  components: {
    AppNavbar,
    CardProduct,
    AppFooter,
    ModalDetail
  },
  data() {
    return {
      products: [],
      bestproducts: [],
      search: '',
      modalId: "modalId",
      url: "127.0.0.1",
    }
  },
  methods: {
    setProduct(data) {
      this.products = data
    },
    setBestProduct(data) {
      this.bestproducts = data
    },
    searchProduct(){
      axios.get('http://'+this.url+'/products/'+this.search)
      .then((response) => {
        //console.log("Success: ",response.data.data);
        this.setProduct(response.data.data);
      }).catch ((err) =>{
        console.log(err)
      });
    }
  },
  mounted() {
    axios.get('http://'+this.url+'/products')
    .then((response) => {
      //console.log("Success: ",response.data.data);
      this.setProduct(response.data.data);
    }).catch ((err) =>{
      console.log(err)
    });

    // axios.get('http://192.168.130.215/bestproducts')
    // .then((response) => {
    //   console.log("Success: ",response.data.data);
    //   this.setBestProduct(response.data.data);
    // }).catch ((err) =>{
    //   console.log(err)
    // });

  }
}
</script>