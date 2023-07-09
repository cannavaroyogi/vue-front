<template>
    <div class="card shadow card-product" >
        <img class="card-img-top" v-bind:src="product.image" alt="Card image cap" width="1%">
            <div class="card-body">
                <h5 class="card-title">{{ product.name_product }}</h5>
                <p class="card-text">Harga : Rp. {{product.price}}</p>
                <a href="#" class="btn btn-danger">Tambah ke koleksi</a>
            </div>
    </div>
</template>

<script>
export default {
    name: 'CardProduct',
    props: ["product"]
}
</script>

<style>

</style>