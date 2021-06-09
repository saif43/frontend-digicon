<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark container">
    <div class="container-fluid">
      <h4 class="navbar-brand">Cart</h4>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarScroll"
        aria-controls="navbarScroll"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div
        class="collapse navbar-collapse justify-content-end"
        id="navbarScroll"
      >
        <ul class="navbar-nav mr-auto"></ul>
        <ul class="navbar-nav" style="--bs-scroll-height: 100px">
          <li class="nav-item">
            <button type="button" class="btn btn-sm btn-danger">Logout</button>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Navbar",
};
</script>

<style scoped>
.btn-danger {
  background: rgb(110, 8, 8);
  border-color: rgb(110, 8, 8);
}

.btn-danger:hover {
  background: rgb(184, 35, 35);
  border-color: rgb(184, 35, 35);
}
</style>