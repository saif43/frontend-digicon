<template>
  <div class="col-sm-4 left">
    <h3 class="mb-4">Product list</h3>
    <Product />
    <Product />
    <Product />
  </div>
</template>

<script>
import Product from "./Product.vue";

export default {
  name: "Products",
  components: {
    Product,
  },
};
</script>

<style scoped>
.left {
  border-right: rgb(224, 224, 224) solid 1px;
}
</style>