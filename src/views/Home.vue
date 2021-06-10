<template>
  <div v-if="!isSignedIn && !access">
    <Auth
      :showSignUp="showSignUp"
      @sign-in="signIn"
      @toggle-sign-up="toggleSignup"
    />
  </div>
  <div v-else>
    <Dashboard :access="access" @sign-out="signOut" />
  </div>
</template>

<script>
import Dashboard from "../components/Dashboard.vue";
import Auth from "../components/Auth.vue";

export default {
  name: "Home",
  components: {
    Auth,
    Dashboard,
  },
  data() {
    return {
      isSignedIn: false,
      showSignUp: false,
      access: localStorage.getItem("access"),
    };
  },
  methods: {
    toggleSignup() {
      this.showSignUp = !this.showSignUp;
    },
    signIn() {
      this.access = localStorage.getItem("access");
      this.isSignedIn = true;
    },
    signOut() {
      localStorage.removeItem("access");
      localStorage.removeItem("refresh");

      this.access = null;
      this.isSignedIn = false;
    },
  },
};
</script>


