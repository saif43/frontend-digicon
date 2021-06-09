<template>
  <div class="col-sm-4 right">
    <h3 class="mb-4">Cart</h3>
    <!-- <h4>Cart is Empty</h4> -->
    <CartItem />
    <CartItem />
    <CartItem />
  </div>
</template>

<script>
import CartItem from "./CartItem.vue";

export default {
  name: "Cart",
  components: {
    CartItem,
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