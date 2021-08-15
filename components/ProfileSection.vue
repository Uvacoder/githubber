<template>
  <div>
    <div class="h-100 d-flex flex-column align-items-cente">
      <img
        class="img-fluid align-self-center rounded-circle shadow"
        width="150px"
        :src="ghProfile.avatar_url"
        v-bind:alt="ghProfile.login + '\'s profile Image'"
      />

      <div class="container mt-3">
        <div class="row">
          <div class="col-md-6 d-flex justify-content-center">
            <div class="">
              <span class="h5">Full Name: </span
              ><span class="ms-1">{{ ghProfile.name }}</span>
            </div>
          </div>

          <div class="col-md-6 d-flex justify-content-center">
            <span class="h5">Username: </span
            ><span class="ms-1">{{ ghProfile.login }}</span>
          </div>

          <div class="col-md-12 d-flex justify-content-center">
            <span class="h5"> GitHub Link: </span
            ><span class="ms-1"
              ><a v-bind:href="ghProfile.html_url" target="_blank">{{
                ghProfile.login
              }}</a></span
            >
          </div>

          <div class="col-md-12 d-flex justify-content-center">
            <span class="h5"> Location: </span
            ><span class="ms-1" v-if="ghProfile.location">
              {{ ghProfile.location }}</span
            >
            <span class="ms-1 text-danger fw-bold" v-else>not available</span>
          </div>

          <div class="col-md-12 d-flex justify-content-center">
            <span class="h5"> Email: </span
            ><span class="ms-1" v-if="ghProfile.email">
              {{ ghProfile.email }}</span
            >
            <span class="ms-1 text-danger fw-bold" v-else>not available</span>
          </div>

          <div class="col-md-12 d-flex justify-content-center">
            <div class="mt-2">
              <div class="text-center h5">Bio</div>
              <div v-if="ghProfile.bio">{{ ghProfile.bio }}</div>
              <div class="text-danger fw-bold" v-else>not available</div>
            </div>
          </div>

          <div class="mt-4">
            <div class="row">
              <div
                class="col-lg-3 col-md-3 col-6 d-flex justify-content-center"
              >
                <div>
                  <span class="me-1 fs-5 fw-bold">Repos: </span>
                  {{ ghProfile.public_repos }}
                </div>
              </div>

              <div
                class="col-lg-3 col-md-3 col-6 d-flex justify-content-center"
              >
                <div>
                  <span class="me-1 fs-5 fw-bold"> Gists: </span
                  >{{ ghProfile.public_gists }}
                </div>
              </div>

              <div
                class="col-lg-3 col-md-3 col-6 d-flex justify-content-center"
              >
                <div>
                  <span class="me-1 fs-5 fw-bold"> Followers: </span
                  >{{ ghProfile.followers }}
                </div>
              </div>

              <div
                class="col-lg-3 col-md-3 col-6 d-flex justify-content-center"
              >
                <div>
                  <span class="me-1 fs-5 fw-bold"> Following: </span
                  >{{ ghProfile.following }}
                </div>
              </div>
            </div>
          </div>

          <!-- <div>{{ ghProfile.public_repos }}</div>
            <div>{{ ghProfile.public_gists }}</div>
            <div>{{ ghProfile.followers }}</div>
            <div>{{ ghProfile.following }}</div> -->
        </div>
      </div>
      <!-- User Profile Data from GitHub End -->
      <RepoSection class="mt-3" v-bind:ghRepo="ghRepo" />
      <!-- User Profile Data from GitHub End -->
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProfileSection',
  props: ['ghProfile', 'ghRepo'],
}
</script>
