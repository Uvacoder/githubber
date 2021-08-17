<template>
  <div>
    <div class="container">
      <!-- navbar -->
      <NavBar />
      <!-- navbar -->

      <!-- GitHub Username form Start -->
      <div class="row mt-5 d-flex justify-content-center">
        <div class="col-lg-7 col-md-6">
          <!-- Takes GitHub Username -->
          <input
            type="text"
            class="form-control mb-4"
            v-model="ghUser"
            autocomplete="off"
            placeholder="Enter GitHub Username"
          />

          <!-- Sends username for Processing -->
          <button class="btn btn-primary" @click="fetchGHData">Search</button>
          <!-- Sends username for Processing -->

          <!-- Resets the Page -->
          <button class="btn btn-danger" @click="reset">Reset</button>
          <!-- Resets the Page -->
        </div>
      </div>
      <!-- GitHub Username form End -->

      <hr />

      <!-- Welcome/Reset Screen -->
      <div class="d-flex flex-column align-items-center" v-if="ghProfile == ''">
        <h2>Enter the GitHub Username to Search</h2>
      </div>
      <!-- Welcome/Reset Screen -->

      <!-- Shows if User not Found -->
      <UserNotFound v-bind:ghUser="ghUser" v-else-if="ghProfile.message" />
      <!-- Shows if User not Found -->

      <!-- Show if User Found -->
      <ProfileSection
        v-bind:ghProfile="ghProfile"
        v-bind:ghRepo="ghRepo"
        v-else
      />
      <!-- Show if User Found -->

      <!-- Footer -->
      <Footer />
      <!-- Footer -->
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      ghProfile: [],
      ghRepo: [],
      ghUser: '',
      ghToken: process.env.GHTOKEN,
    }
  },
  methods: {
    fetchGHData() {
      this.fetchGHProfile()
      this.fetchGHRepo()
    },
    //! Fetch User Profile
    async fetchGHProfile() {
      this.ghProfile = await fetch(
        `https://api.github.com/users/${this.ghUser}?${this.ghToken}`,
        {}
      )
        .then((res) => res.json())
        .catch((res) => {
          console.log(res)
        })
    },
    //! Fetch User Repo
    async fetchGHRepo() {
      this.ghRepo = await fetch(
        `https://api.github.com/users/${this.ghUser}/repos?${this.ghToken}`,
        {}
      )
        .then((res) => res.json())
        .catch((res) => {
          console.log(res)
        })
    },
    //! Reset Page
    reset() {
      this.ghProfile = ''
      this.ghUser = ''
    },
  },
}
</script>
