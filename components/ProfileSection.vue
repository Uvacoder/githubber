<template>
  <!-- Profile Section Start -->
  <div>
    <div class="h-100 d-flex flex-column align-items-cente">
      <!-- User Image -->
      <img
        class="img-fluid align-self-center rounded-circle shadow"
        width="150px"
        :src="ghProfile.avatar_url"
        v-bind:alt="ghProfile.login + '\'s profile Image'"
      />
      <!-- User Image -->

      <!-- Profile Data like Name etc -->
      <div class="container mt-3">
        <div class="row">
          <div class="col-md-6 d-flex justify-content-center">
            <!-- User's real name as they set in GitHub -->
            <div>
              <span class="h5">Name: </span
              ><span class="ms-1">{{ ghProfile.name }}</span>
            </div>
          </div>

          <!-- User's Username as they set in GitHub -->
          <div class="col-md-6 d-flex justify-content-center">
            <span class="h5">Username: </span
            ><span class="ms-1">{{ ghProfile.login }}</span>
          </div>

          <!-- User's GitHub Link -->
          <div class="col-md-12 d-flex justify-content-center">
            <span class="h5"> GitHub Link: </span
            ><span class="ms-1"
              ><a v-bind:href="ghProfile.html_url" target="_blank">{{
                ghProfile.login
              }}</a></span
            >
          </div>

          <!-- User's Location as they set in GitHub -->
          <div class="col-md-12 d-flex justify-content-center">
            <span class="h5"> Location: </span>

            <!-- Shows Location if available -->
            <span class="ms-1" v-if="ghProfile.location">
              {{ ghProfile.location }}</span
            >

            <!-- Shows if no location is available -->
            <span class="ms-1 text-danger fw-bold" v-else>not available</span>
          </div>

          <!-- User's Email as they set in GitHub -->
          <div class="col-md-12 d-flex justify-content-center">
            <span class="h5"> Email: </span>

            <!-- Shows Email if available -->
            <span class="ms-1" v-if="ghProfile.email">
              {{ ghProfile.email }}</span
            >

            <!-- Shows if no Email is available -->
            <span class="ms-1 text-danger fw-bold" v-else>not available</span>
          </div>

          <!-- User's Bio as they set in GitHub -->
          <div class="col-md-12 d-flex justify-content-center">
            <div class="mt-2">
              <div class="text-center h5">Bio</div>

              <!-- Shows if Bio is available -->
              <div v-if="ghProfile.bio">{{ ghProfile.bio }}</div>

              <!-- Shows if no Bio is available -->
              <div class="text-danger fw-bold" v-else>not available</div>
            </div>
          </div>

          <!-- Additional stats like number of repos and Gists
               Note: Only Public Information is shown -->
          <div class="mt-4">
            <div class="row">
              <!-- Shows total number of Repos -->
              <div
                class="col-lg-3 col-md-3 col-6 d-flex justify-content-center"
              >
                <div>
                  <span class="me-1 fs-5 fw-bold">Repos: </span>
                  {{ ghProfile.public_repos }}
                </div>
              </div>

              <!-- Shows total number of Gists -->
              <div
                class="col-lg-3 col-md-3 col-6 d-flex justify-content-center"
              >
                <div>
                  <span class="me-1 fs-5 fw-bold"> Gists: </span
                  >{{ ghProfile.public_gists }}
                </div>
              </div>

              <!-- Shows total number of Followers -->
              <div
                class="col-lg-3 col-md-3 col-6 d-flex justify-content-center"
              >
                <div>
                  <span class="me-1 fs-5 fw-bold"> Followers: </span
                  >{{ ghProfile.followers }}
                </div>
              </div>

              <!-- Shows total number of Followings -->
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
        </div>
      </div>

      <!-- User Repo Data from GitHub Start -->
      <RepoSection class="mt-3" v-bind:ghRepo="ghRepo" />
      <!-- User Repo Data from GitHub End -->
    </div>
  </div>
  <!-- Profile Section Start -->
</template>

<script>
export default {
  name: 'ProfileSection',
  props: ['ghProfile', 'ghRepo'],
}
</script>
