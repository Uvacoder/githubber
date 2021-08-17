<template>
  <div class="d-flex flex-column align-items-center">
    <!-- Error Background -->
    <div class="bg-imag bg-im position-relative">
      <!-- Error Image -->
      <img class="img-fluid" src="~/assets/images/undraw_No_data.svg" alt="" />

      <!-- Error Message -->
      <div class="text-center position-absolute top-50 error-pos">
        No user by the name of "<span class="fw-bold text-break">
          {{ ghUser }}</span
        >" exist on GitHub
      </div>
    </div>
    <!-- Error Background -->
  </div>
</template>

<script>
export default {
  name: 'UserNotFound',
  props: ['ghUser'],
}
</script>

<style scoped>
.error-pos {
  left: 40%;
  right: 5%;
}
</style>
