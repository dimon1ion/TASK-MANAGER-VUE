<template>
  <div class="container w-50" id="con" style="margin-top: 20vh">
    <div class="row">
      <div class="col-12">
        <h1>
          Todo List:
          <span
            :style="[
              countTasks > 10
                ? { backgroundColor: 'red', color: 'white' }
                : {},
            ]"
            >{{ countTasks }}</span
          >
        </h1>
      </div>
    </div>
    <div class="row">
      <div class="col" style="margin-bottom: 20px">
        <div class="input-group mb-3">
          <input
            type="text"
            class="form-control"
            placeholder="Add New Task ..."
            aria-describedby="button-addon2"
            id="inputText"
            v-model="text"
          />
          <button class="btn btn-primary" type="button" @click="AddItem">
            +
          </button>
        </div>
      </div>
    </div>
    <div
      class="row showItem"
      style="border-bottom: 0.5px solid lightgray; margin-bottom: 5px"
      v-for="task in tasks"
    >
      <Task :task="task">
        <button class="btn btn-danger" @click="RemoveItem(task)">🗑</button>
      </Task>
    </div>
  </div>
</template>

<script>
import Task from "./Task.vue";

class TaskInfo {
  touched;
  text;
  completed;

  constructor(text) {
    this.text = text;
    this.touched = false;
    this.completed = false;
  }
}

export default {
  name: "TaskManager",
  data() {
    return {
      text: "",
      tasks: [],
    };
  },
  computed: {
    countTasks() {
      return this.tasks.length;
    },
  },
  methods: {
    AddItem() {
      if (this.text != "") {
        this.tasks.push(new TaskInfo(this.text));
      }
    },
    RemoveItem(deleteTask) {
      this.tasks = this.tasks.filter((task) => task !== deleteTask);
    },
  },
  components: { Task },
};
</script>

<style scoped lang="scss"></style>
