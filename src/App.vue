<template>
  <Home :isSignedIn="isSignedIn" />
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

