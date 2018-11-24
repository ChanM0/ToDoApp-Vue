<template>
  <div class="pannel pannel-default">
    <div class="pannel-body">
      {{ qt.content }}
    </div>
    <div class="pannel-footer">
      <div v-if="editing">
        <input type="text">
        <a @click="onUpdate">Save</a>
        <a @click="onCancel">Cancel</a>
      </div>
      <div v-if="!editing">
        <a @click="onEdit">Edit</a>
        <a @click="onDelete">Delete</a>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  props: ["qt"],
  data() {
    return {
      editing: false,
      editValue: this.qt.content
    };
  },
  methods: {
    onEdit() {
      this.editing = true;
      this.editValue = this.qt.content;
    },
    onCancel() {
      this.editing = false;
    },
    onDelete() {
      const token = localStorage.getItem("token");
      this.$emit("quoteDeleted", this.qt.id);
      var path =
        "http://localhost:8888/ApplicationCreation/ToDoApp/public/api/quote/" +
        this.qt.id +
        "?token=" +
        token;
      axios
        .delete(path)
        .then(respose => console.log(response))
        .catch(error => console.log(error));
    },
    onUpdate() {
      this.editing = false;
      this.qt.content = this.editValue;
      const token = localStorage.getItem("token");
      var path =
        "http://localhost:8888/ApplicationCreation/ToDoApp/public/api/quote/" +
        this.qt.id +
        "?token=" +
        token;
      axios
        .put(path, {
          content: this.editValue
        })
        .then(respose => console.log(response))
        .catch(error => console.log(error));
    }
  }
};
</script>

<style scoped>
a {
  cursor: pointer;
}
</style>
