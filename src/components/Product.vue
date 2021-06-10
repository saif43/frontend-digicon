<template>
  <div>
    <div class="product">
      <h5>{{ product.name }}</h5>

      <div v-if="product.added_to_cart">
        <button class="btn btn-secondary" disabled>Added</button>
      </div>
      <div v-else>
        <button
          @click="$emit('add-to-cart')"
          class="btn btn-primary added-to-cart"
        >
          Add to cart
        </button>
      </div>
    </div>
    <hr />
  </div>
</template>

<script>
import Fragment from "vue-fragment";

export default {
  name: "Product",
  props: {
    product: Object,
  },
  components: {
    Fragment,
  },
};
</script>

<style scoped>
.product {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>