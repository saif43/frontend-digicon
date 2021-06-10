<template>
  <div v-if="!isSignedIn">
    <Auth
      :showSignUp="showSignUp"
      @sign-in="signIn"
      @toggle-sign-up="toggleSignup"
    />
  </div>
  <div v-else>
    <Dashboard @sign-out="signOut" />
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
    };
  },
  methods: {
    toggleSignup() {
      console.log(1234);
      this.showSignUp = !this.showSignUp;
    },
    signIn() {
      this.isSignedIn = true;
    },
    signOut() {
      localStorage.removeItem("access");
      localStorage.removeItem("refresh");

      this.isSignedIn = false;
    },
  },
};
</script>


