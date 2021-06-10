<template>
  <div class="col-sm-4 left">
    <h3 class="mb-4">Product list</h3>
    <div v-for="product in products" :key="product.id">
      <Product
        :product="product"
        @add-to-cart="$emit('add-to-cart', product.id)"
      />
    </div>
  </div>
</template>

<script>
import Product from "./Product.vue";

export default {
  name: "Products",
  components: {
    Product,
  },
  props: {
    products: Array,
  },
};
</script>

<style scoped>
.left {
  border-right: rgb(224, 224, 224) solid 1px;
}
</style>