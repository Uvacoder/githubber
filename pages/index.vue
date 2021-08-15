<template>
  <div>
    <div class="container">
      <!-- navbar -->
      <NavBar />

      <!-- GitHub Username form -->
      <div class="row mt-5 d-flex justify-content-center">
        <div class="col-lg-7 col-md-6">
          <input
            type="text"
            class="form-control mb-4"
            v-model="ghUser"
            autocomplete="off"
            placeholder="Enter GitHub Username"
          />
          <button class="btn btn-primary" @click="fetchGHData">Search</button>
          <button class="btn btn-danger" @click="reset">Reset</button>
          <!-- calling fetch() -->
        </div>
      </div>

      <hr />

      <div class="d-flex flex-column align-items-center" v-if="ghProfile == ''">
        <h2>Enter the GitHub Username to Search</h2>
      </div>
      <UserNotFound
        v-bind:ghProfile="ghProfile"
        v-bind:ghUser="ghUser"
        v-else-if="ghProfile.message"
      />
      <!-- User Profile Data from GitHub End -->
      <ProfileSection
        v-bind:ghProfile="ghProfile"
        v-bind:ghRepo="ghRepo"
        v-else
      />
      <!-- {{ ghRepo }} -->
      <!-- User Profile Data from GitHub End -->
      <Footer />
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
        'https://api.github.com/users/' + this.ghUser,
        {
          headers: {
            authorization: 'token ' + this.ghToken,
          },
        }
      )
        .then((res) => res.json())
        .catch((res) => {
          console.log(res)
        })
    },
    //! Fetch User Repo
    async fetchGHRepo() {
      this.ghRepo = await fetch(
        'https://api.github.com/users/' + this.ghUser + '/repos',
        {
          headers: {
            authorization: 'token ' + this.ghToken,
          },
        }
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
