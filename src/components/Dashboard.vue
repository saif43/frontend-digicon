<template>
  <Navbar @sign-out="$emit('sign-out')" />
  <div class="container">
    <div class="row">
      <Products :products="products" @add-to-cart="addToCart" />
      <Cart :cart="cart" @remove-from-cart="removeFromCart" />
    </div>
  </div>
</template>

<script>
import Navbar from "./Navbar.vue";
import Products from "./Products.vue";
import Cart from "./Cart.vue";
import backend from "../../api/backend";

export default {
  name: "Dashboard",
  components: {
    Navbar,
    Products,
    Cart,
  },
  props: {
    access: String,
  },
  async created() {
    this.products = await this.fetchProducts();
    this.cart = await this.fetchCart();
  },
  data() {
    return {
      products: [],
      cart: [],
    };
  },
  methods: {
    async addToCart(id) {
      const config = {
        headers: { Authorization: `JWT ${this.access}` },
      };

      const { data, status } = await backend.post(
        "user/cart/",
        { product: id },
        config
      );

      const { product } = data;

      if (status === 201) {
        this.cart = [...this.cart, data];

        this.products = this.products.map((item) =>
          item.id === product.id ? { ...item, added_to_cart: true } : item
        );
      }
    },

    async removeFromCart(id) {
      const config = {
        headers: { Authorization: `JWT ${this.access}` },
      };

      const { status } = await backend.delete(`user/cart/${id}/`, config);

      if (status === 200 || status === 204) {
        const removed_item = this.cart.filter((item) => item.id === id);

        this.cart = this.cart.filter((item) => item.id !== id);

        this.products = this.products.map((item) =>
          item.id === removed_item[0].product.id
            ? { ...item, added_to_cart: false }
            : item
        );
      }
    },

    async fetchCart() {
      const config = {
        headers: { Authorization: `JWT ${this.access}` },
      };

      const { data } = await backend.get("user/cart/", config);
      return data;
    },

    async fetchProducts() {
      const config = {
        headers: { Authorization: `JWT ${this.access}` },
      };

      const { data } = await backend.get("product/", config);
      return data;
    },
  },
};
</script>

<style scoped>
.row {
  margin-top: 2%;
  height: 90vh;
}
</style>