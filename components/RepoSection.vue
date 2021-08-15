<template>
  <div>
    <h2 class="text-center mb-3">Repo Cards</h2>
    <div class="row">
      <div
        id="Test"
        v-for="item in ghRepo"
        :key="item"
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
            <h5 class="card-title">{{ item.full_name }}</h5>
            <p class="card-text">
              <span v-if="item.description">{{ item.description }}</span>
              <span class="text-danger" v-else>No Description Available</span>
            </p>
            <div class="d-flex flex-row">
              <div class="text-primary me-2">
                <i class="fas fa-code-branch"></i> {{ item.forks }}
              </div>

              <div class="text-primary me-2">
                <i class="far fa-star"></i> {{ item.stargazers_count }}
              </div>

              <div class="text-primary me-2">
                <i class="far fa-eye"></i> {{ item.watchers_count }}
              </div>
            </div>
            <a
              class="mt-2"
              v-bind:href="item.homepage"
              target="_blank"
              v-if="item.homepage"
              >Open Linked Website</a
            >
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
        <!-- {{ item.full_name }} {{ item.forks }} {{ item.stargazers_count }}
      {{ item.watchers_count }} {{ item.html_url }} -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'RepoSection',
  props: ['ghRepo', 'ghUser'],
}
</script>

<style scoped>
.round {
  border-radius: 0.6rem;
}

.border-primary {
  transition: ease 1s;
}
.border-primary:hover {
  transform: translateY(-15px);
  border-color: transparent !important;
}
</style>
