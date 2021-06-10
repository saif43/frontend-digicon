<template>
  <div v-if="showSignUp">
    <Signup @toggle-sign-up="$emit('toggle-sign-up')" />
  </div>
  <div v-else>
    <Login
      @toggle-sign-up="$emit('toggle-sign-up')"
      @sign-in="$emit('sign-in')"
    />
  </div>
</template>

<script>
import Login from "./Login.vue";
import Signup from "../views/Signup.vue";

export default {
  name: "Auth",
  components: {
    Login,
    Signup,
  },
  props: {
    showSignUp: Boolean,
  },
};
</script>