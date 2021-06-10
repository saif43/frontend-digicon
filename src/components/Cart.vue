<template>
  <div class="col-sm-4 right">
    <h3 class="mb-4">Cart</h3>
    <div v-if="cart.length">
      <div v-for="item in cart" :key="item.id">
        <CartItem :item="item" @remove-from-cart="$emit('remove-from-cart', item.id)" />
      </div>
    </div>
    <div v-else>
      <h4>Cart is Empty</h4>
    </div>
  </div>
</template>

<script>
import CartItem from "./CartItem.vue";

export default {
  name: "Cart",
  components: {
    CartItem,
  },
  props: {
    cart: Array,
  },
};
</script>

<style scoped>
.right {
  margin-left: 3%;
}

h4 {
  color: rgba(112, 112, 112, 0.445);
}
</style>