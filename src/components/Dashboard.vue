<template>
  <Navbar />
  <div class="container">
    <div class="row">
      <Products />
      <Cart />
    </div>
  </div>
</template>

<script>
import Navbar from "./Navbar.vue";
import Products from "./Products.vue";
import Cart from "./Cart.vue";

export default {
  name: "Dashboard",
  components: {
    Navbar,
    Products,
    Cart,
  },
};
</script>

<style scoped>
.row {
  margin-top: 2%;
  height: 90vh;
}
</style>