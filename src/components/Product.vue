<template>
  <div>
    <div class="product">
      <h5>Product 1</h5>
      <button class="btn btn-primary">Add to cart</button>
    </div>
    <hr />
  </div>
</template>

<script>
export default {
  name: "Product",
};
</script>

<style scoped>
.product {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.product button {
  margin-right: 9%;
}
</style>