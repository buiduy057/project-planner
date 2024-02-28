<template>
  <div class="home">
    <div v-if="projects.length">
      <div v-for="project in projects" :key="project.id">
        <SingleProject :project="project" @delete="handleDelete" />
      </div>
    </div>
  </div>
</template>
<script>
import SingleProject from "@/components/SingleProject.vue";
export default {
  components: { SingleProject },
  data() {
    return {
      projects: [],
    };
  },
  mounted() {
    this.loadData();
  },
  methods: {
    loadData() {
      fetch("http://localhost:3000/projects")
        .then((response) => {
          return response.json();
        })
        .then((data) => {
          this.projects = data;
        })
        .catch((error) => {
          // Handle errors
          console.error("Error:", error);
        });
    },
    handleDelete(id) {
      this.projects = this.projects.filter((project) => project.id !== id);
    },
  },
};
</script>
