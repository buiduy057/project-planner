<template>
  <div class="project">
    <div class="actions">
      <h3 @click="showDetail = !showDetail">
        {{ project.title }}
      </h3>
    </div>
    <div v-if="showDetail" class="detail">
      <p>{{ project.detail }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["project"],
  data() {
    return {
      showDetail: false,
    };
  },
};
</script>

<style>
.project {
  margin: 20px auto;
  background: #fff;
  padding: 10px 20px;
  border-radius: 4px;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.5);
  border-left: 4px solid #e90074;
}
h3 {
  cursor: pointer;
}
</style>
