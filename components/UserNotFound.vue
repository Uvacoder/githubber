<template>
  <div class="d-flex flex-column align-items-center">
    <!-- Background image -->
    <div class="bg-imag bg-im position-relative">
      <img class="img-fluid" src="~/assets/images/undraw_No_data.svg" alt="" />
      <div class="text-center position-absolute top-50 error-pos">
        No user by the name of "<span class="fw-bold text-break">
          {{ ghUser }}</span
        >" exist on GitHub
      </div>
    </div>
    <!-- Background image -->
  </div>
</template>

<script>
export default {
  name: 'UserNotFound',
  props: ['ghProfile', 'ghUser'],
}
</script>

<style scoped>
/* .bg-image {
  background-image: url('~assets/images/undraw_No_data.svg');
  height: 100vh;
  width: 100%;
} */
.error-pos {
  left: 40%;
  right: 5%;
}
</style>
