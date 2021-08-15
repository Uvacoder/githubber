<template>
  <div>
    <!-- Footer -->
    <footer class="bg-ligh text-center text-lg-start">
      <!-- Grid container -->
      <div class="container p-4"></div>
      <!-- Grid container -->

      <!-- Copyright -->
      <div class="text-center p-3">
        wrench1815 © {{ footerYear }}
        | built using
        <a class="text-link" href="https://nuxtjs.org/" target="_blank">Nuxt</a>
        and
        <a class="text-link" href="https://mdbootstrap.com/" target="_blank"
          >MDB</a
        >
      </div>
      <div class="text-center">
        <a
          class="d-inline text-white py-1 px-2 rounded-3 github-bg"
          href="https://github.com/wrench1815"
          target="_blank"
        >
          Source Code <i class="fab fa-github"></i>
        </a>
      </div>
      <!-- Copyright -->
    </footer>
    <!-- Footer -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      footerYear: new Date().getFullYear(),
    }
  },
}
</script>

<style scoped>
.github-bg {
  background-color: #333;
}
</style>
