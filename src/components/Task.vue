<template>
  <section :class="[task.reminder ? 'reminder' : '']">
    <h3 class="h3" v-if="!updateStatus">
      <span>{{ index + 1 }}</span>
      <span>{{ task.text }}</span>
    </h3>
    <h3 class="h3" v-if="updateStatus">
      <input
        type="text"
        style="margin-left: 10px"
        v-model="newText"
        :placeholder="task.text"
      />
    </h3>
    <div class="checkbox-holder" v-if="updateStatus">
      <label :for="`reminder${task.id}`"> reminder </label>
      <input
        type="checkbox"
        name="reminder"
        :id="`reminder${task.id}`"
        v-bind:checked="task.reminder"
        v-model="checked"
      />
    </div>
    <div class="btn-holder">
      <Button
        title="UPDATE"
        color="#0000ff91"
        @click="onUpdate(task.id)"
        v-if="!updateStatus"
      />
      <Button
        title="CONFIRM"
        color="#097c3991"
        @click="onConfirm(newText, checked)"
        v-show="updateStatus"
      />
      <Button
        title="DELETE"
        color="#c71921ba"
        @click="onDelete(task.id)"
        v-if="!updateStatus"
      />
      <Button
        title="DISCARD"
        color="#c88514ba"
        @click="onDiscard()"
        v-if="updateStatus"
      />
    </div>
  </section>
</template>
<script>
import Button from "./Button.vue";

export default {
  name: "Task",
  data() {
    return {
      updateStatus: false,
      newText: this.task.text,
      checked: this.task.reminder,
    };
  },
  props: {
    task: Object,
    index: Number,
  },
  components: {
    Button,
  },
  methods: {
    onDelete: function (id) {
      this.$emit("delete-task", id);
    },
    onUpdate: function (id) {
      this.updateStatus = !this.updateStatus;
    },
    onDiscard: function () {
      this.updateStatus = !this.updateStatus;
    },
    onConfirm: function (newText, checked) {
      this.updateStatus = !this.updateStatus;
      this.$emit("update-task", {
        id: this.task.id,
        text: newText,
        reminder: checked,
      });
    },
  },
};
</script>
<style scoped>
section {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 10px 0;
  background-color: gainsboro;
}
.h3 {
  display: flex;
  justify-content: flex-start;
  align-items: center;
}
.h3 span {
  padding: 0 10px;
}
.reminder {
  border-left: solid 4px green;
}
.checkbox-holder {
  display: flex;
  font-weight: bold;
}
</style>