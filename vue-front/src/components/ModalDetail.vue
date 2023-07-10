<template>
    <div>
      <b-modal :id="product.code_product" hide-footer size="xl" :title="product.name_product">
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