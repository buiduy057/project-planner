<template>
  <div class="project">
    <div class="actions">
      <h3 @click="showDetail = !showDetail">
        {{ project.title }}
      </h3>
      <div class="icons">
        <EditOutlined />
        <DeleteOutlined @click="deleteProject" />
        <CheckOutlined />
      </div>
    </div>
    <div v-if="showDetail" class="detail">
      <p>{{ project.detail }}</p>
    </div>
  </div>
</template>

<script>
import {
  CheckOutlined,
  EditOutlined,
  DeleteOutlined,
} from "@ant-design/icons-vue";

export default {
  props: ["project"],
  components: {
    CheckOutlined,
    EditOutlined,
    DeleteOutlined,
  },
  data() {
    return {
      showDetail: false,
      url: "http://localhost:3000/projects/" + this.project.id,
    };
  },
  methods: {
    deleteProject() {
      fetch(this.url, { method: "DELETE" }).then(() =>
        this.$emit("delete", this.project.id)
      );
    },
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
.actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.icons svg {
  font-size: 20px;
  margin-left: 10px;
  color: #bbb;
  cursor: pointer;
}
.icons svg:hover {
  color: #777;
}
</style>
