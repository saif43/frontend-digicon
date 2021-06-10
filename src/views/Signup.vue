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
      <h1 class="h3 mb-3 fw-normal">Sign up</h1>

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
      <div class="form-floating mb-4">
        <input
          type="text"
          class="form-control"
          placeholder="Enter your full name"
          v-model="name"
          required
        />
        <label for="floatingInput">Full name</label>
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

      <button class="w-100 btn btn-lg btn-primary">Sign up</button>
    </form>
    <p class="mt-5 mb-3 text-muted">
      Already have an account ?
      <button
        class="btn btn-outline-secondary"
        @click="$emit('toggle-sign-up')"
      >
        Sign in
      </button>
    </p>
  </main>
</template>

<script>
import backend from "../../api/backend";

export default {
  name: "Signup",
  data() {
    return {
      name: "",
      username: "",
      password: "",
    };
  },
  methods: {
    async onSubmit(e) {
      e.preventDefault();

      const formData = {
        name: this.name,
        username: this.username,
        password: this.password,
      };

      this.name = "";
      this.username = "";
      this.password = "";

      try {
        const { status } = await backend.post("user/create/", formData);

        if (status === 201) {
          this.$emit("toggle-sign-up");
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