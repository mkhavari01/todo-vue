<template >
  <header>
    <input name="taskDesc" v-model="taskDescription" />
    <div>
      <Button
        title="Add Task"
        color="gainsboro"
        @click="addTaskHandler(taskDescription)"
      />
      <!-- <p>Message is: {{ message }}</p> -->
      <!-- <Button title="Update Task" color="#0000ff91" />
            <Button title="delete Task" color="#15be41" /> -->
    </div>
  </header>
</template>
<script>
import Button from "./Button.vue";

export default {
  name: "Header",
  props: {
    title: String,
  },
  components: {
    Button,
  },
  methods: {
    addTaskHandler: function (desc) {
      this.$emit("add-task", desc);
    },
  },
  data() {
    return {
      taskDescription: "",
    };
  },
};
</script>
<style scope>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
input {
  padding: 10px;
  font-size: 16px;
  outline: none;
}
</style>