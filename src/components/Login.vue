<template>
  <main class="form-signin text-center mt-4">
    <form @submit="onSubmit">
      <img
        class="mb-4"
        src="https://getbootstrap.com/docs/5.0/assets/brand/bootstrap-logo.svg"
        alt=""
        width="72"
        height="57"
      />
      <h1 class="h3 mb-3 fw-normal">Please sign in</h1>

      <div class="form-floating mb-4">
        <input
          type="text"
          class="form-control"
          placeholder="name@example.com"
          v-model="username"
          required
        />
        <label for="floatingInput">Username</label>
      </div>
      <div class="form-floating mb-3">
        <input
          type="password"
          v-model="password"
          class="form-control"
          placeholder="Password"
          required
        />
        <label for="floatingPassword">Password</label>
      </div>

      <button class="w-100 btn btn-lg btn-primary">Sign in</button>
    </form>
    <p class="mt-5 mb-3 text-muted">
      New Here ?
      <button
        @click="$emit('toggle-sign-up')"
        class="btn btn-outline-secondary"
      >
        Sign up
      </button>
    </p>
  </main>
</template>


<script>
import backend from "../../api/backend";

export default {
  name: "Login",
  data() {
    return {
      username: "",
      password: "",
    };
  },
  methods: {
    async onSubmit(e) {
      e.preventDefault();

      const formData = {
        username: this.username,
        password: this.password,
      };

      this.username = "";
      this.password = "";

      try {
        const { data, status } = await backend.post("token/", formData);

        if (status === 200) {
          const { refresh, access } = data;

          localStorage.setItem("access", access);
          localStorage.setItem("refresh", refresh);

          this.$emit("sign-in");
        }
      } catch (error) {
        console.log(error);
        console.log(error.response);
      }
    },
  },
};
</script>

<style scoped>
.form-signin {
  margin: 0 30%;
}
</style>