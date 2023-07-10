<template>
    <div>
      <b-modal :id="product.code_product" title="BootstrapVue">
        <p class="my-4">{{ product.name_product }}</p>
      </b-modal>
    </div>
</template>

<script>
export default {
    name: 'ModalDetail',
    props: ['product','modalId']
}
</script>

<style>

</style>