<template>
  <div>
    <div class="product">
      <h5>{{ item.product.name }}</h5>
      <button
        @click="$emit('remove-from-cart', item.id)"
        class="btn btn-danger"
      >
        Remove
      </button>
    </div>
    <hr />
  </div>
</template>

<script>
export default {
  name: "CartItem",
  props: {
    item: Object,
  },
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