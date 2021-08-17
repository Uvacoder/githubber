<template>
  <!-- Repo Cards Start -->
  <div>
    <h2 class="text-center mb-3">Repo Cards</h2>

    <div class="row">
      <div
        v-for="item in ghRepo"
        :key="item.id"
        class="
          col-lg-4 col-md-6
          mb-5
          d-flex
          justify-content-center
          align-items-center
        "
      >
        <div class="card border border-primary flex-grow-1 round">
          <div class="card-body d-flex flex-column hover-shadow round">
            <!-- Repo Name affixed with login(username) -->
            <h5 class="card-title">{{ item.full_name }}</h5>

            <!-- Repo Description -->
            <p class="card-text pe-none">
              <span v-if="item.description">{{ item.description }}</span>
              <span class="text-danger" v-else>No Description Available</span>
            </p>

            <!-- Section with Forks Stars and Watchers(left) Primary Langauge as calculated by GitHub(right) -->
            <section class="d-flex flex-row pe-none">
              <!-- Shows number of Forks -->
              <div class="text-primary me-2">
                <i class="fas fa-code-branch"></i> {{ item.forks }}
              </div>

              <!-- Shows number of Stars -->
              <div class="text-primary me-2">
                <i class="far fa-star"></i> {{ item.stargazers_count }}
              </div>

              <!-- Shows number of Watchers -->
              <div class="text-primary me-2">
                <i class="far fa-eye"></i> {{ item.watchers_count }}
              </div>

              <!-- Shows Primary Langauge as calculated by GitHub -->
              <div class="ms-auto text-warning" v-if="item.language">
                <p class="border border-warning px-1 rounded-3">
                  {{ item.language }}
                </p>
              </div>
            </section>

            <!-- Shows Website link if linked -->
            <div>
              <a
                class="mt-2"
                v-bind:href="item.homepage"
                target="_blank"
                v-if="item.homepage"
                >Open Linked Website</a
              >
            </div>

            <!-- Button that opens a new tab with the GitHub/reponame -->
            <div class="mt-3">
              <a
                type="button"
                class="btn btn-primary"
                v-bind:href="item.html_url"
                target="_blank"
                >go to repo</a
              >
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <!-- Repo Cards End -->
</template>

<script>
export default {
  name: 'RepoSection',
  props: ['ghRepo'],
}
</script>

<style scoped>
/* Adds round borders to elements */
.round {
  border-radius: 0.6rem;
}

/*
* Inherit the MDB5 border-primary class for further customization 
* sets transition duration
*/
.border-primary {
  transition: ease 1s;
}

/* 
On Hover
* translates element up 15px
* sets border color to #fbfbfb(white)
*/
.border-primary:hover {
  transform: translateY(-15px);
  border-color: #fbfbfb !important;
}
</style>
