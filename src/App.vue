<template>
  <Home :isSignedIn="isSignedIn" />
  <!-- <router-view /> -->
</template>

<script>
import Home from "./views/Home.vue";

export default {
  name: "App",
  props: {
    isSignedIn: false,
  },
  components: {
    Home,
  },
};
</script>

