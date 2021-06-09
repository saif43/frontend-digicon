<template>
  <div v-if="isSignedIn">
    <Login />
  </div>
  <div v-else>
    <Dashboard />
  </div>
</template>

<script>
import Dashboard from "../components/Dashboard.vue";
import Login from "../components/Login.vue";

export default {
  name: "Home",
  components: {
    Login,
    Dashboard,
  },
};
</script>


