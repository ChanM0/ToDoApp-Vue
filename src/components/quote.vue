<template>
  <div class="pannel pannel-default">
    <div class="pannel-body">
      {{ qt.content }}
    </div>
    <div class="pannel-footer">
      <div>
        <input type="text">
        <a href="" @click="onUpdate">Save</a>
        <a href="" @click="onCancel">Save</a>
      </div>
      <div>
        <a href="" @click="onEdit">Edit</a>
        <a href="" @click="onDelete">Delete</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["qt"]
};
</script>