<template>
    <div>
      <b-modal :id="product.code_product" hide-footer size="xl" :title="product.name_product">
        <!-- <p class="my-4">{{ product.name_product }}</p> -->
        <div class="row ml-2">
            <div class="col-sm-3">
              <div class="card shadow" style="width: 15rem; height: 10 rem;">
                <img class="card-image-top" v-bind:src="product.image" alt="Card image cap" loading="lazy"/>
                <div class="card-body">
                  <h5 class="card-title">{{ product.name_product }}</h5>
                  <p class="card-text">Harga : Rp. {{product.price}}</p>
                  <div class="row">
                      <div class="col">
                          <!-- <a href="#" class="btn btn-lg btn-danger"><strong>Detail</strong></a> -->
                          <router-link to="/addkoleksi" class="btn btn-lg btn-danger text-center align-center">Tambah Koleksi<b-icon-plus></b-icon-plus></router-link>
                      </div>
                  </div>
                </div>
              </div>
            </div>
            <div class="col-sm-9">
              <h4><strong>Judul : </strong> {{ product.name_product }} </h4>
              <p></p>
              <h3><strong>Sinopsis: </strong> </h3><br>
              <div v-if="product.sinopsis === null">
                <p> Sinopsis tidak tersedia </p>
              </div>
              <div v-else-if="product.sinopsis !== null">
                <p>{{ product.sinopsis }}</p>
              </div>
            </div>
        </div>
      </b-modal>
    </div>
</template>

<script>
export default {
    name: 'ModalDetail',
    props: ['product','modalId'],
}
</script>

<style>

</style>