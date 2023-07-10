<template>
    <div class="card-product">
        <div class="card shadow card-product" >
            <img class="card-img-top" v-bind:src="product.image" alt="Card image cap" width="300" height="500" loading="lazy">
            <div class="card-body">
                <h5 class="card-title">{{ product.name_product }}</h5>
                <p class="card-text">Harga : Rp. {{product.price}}</p>
                <div class="row">
                    <div class="col">
                        <!-- <a href="#" class="btn btn-lg btn-danger" width="100" height="48" data-toggle="modal" :data-target="`#${modalId}`"><strong>Detail</strong></a> -->
                        <b-button class="btn btn-lg btn-danger" v-b-modal=product.code_product>Detail</b-button>
                    </div>
                    <div class="col">
                        <!-- <a href="#" class="btn btn-lg btn-danger"><strong>Detail</strong></a> -->
                        <router-link to="/addkoleksi" class="btn btn-danger float-right"><b-icon-plus width="30" height="30"></b-icon-plus></router-link>
                    </div>
                </div>
            </div>
        </div>
        <!-- <ModalDetail :modalId="modalId"/> -->
    </div>
</template>
<script>
// import ModalDetail from "@/components/ModalDetail.vue";

export default {
    name: 'CardProduct',
    // components: {
    //      ModalDetail
    //  },
    props: ["product","modalId"],
    methods: {
        openModal() {
            this.$emit('open-modal');
        }
    }
}
</script>

<style>

</style>