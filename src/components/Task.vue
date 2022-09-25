<template>
  <div class="col">
    <h2
      :class="{
        touched: task.completed != true && task.touched,
        completed: task.completed,
      }"
      @click="task.touched = !task.touched"
    >
      {{ task.text }}
    </h2>
  </div>
  <div class="col-3">
    <button
      v-if="!task.completed"
      class="btn btn-success"
      @click="changeStatus"
    >
      ✓
    </button>
    <button v-else class="btn btn-warning" @click="changeStatus">X</button>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "Task",
  data() {
    return {};
  },
  props: {
    task: {
      required: true,
    },
  },
  methods: {
    changeStatus() {
      this.task.completed = !this.task.completed;
    },
  },
};
</script>

<style scoped lang="scss">
h1 {
  text-align: center;
}

.showItem {
  animation-name: showAnim;
  animation-duration: 1s;
  animation-fill-mode: forwards;
  animation-timing-function: ease-in-out;
}

@keyframes showAnim {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.completed {
  animation-name: checkedAnim;
  animation-duration: 1s;
  animation-fill-mode: forwards;
  animation-timing-function: ease-in-out;
}

.touched {
  font-style: italic;
  transition: all 1s;
}

@keyframes checkedAnim {
  to {
    color: lightgray;
    text-decoration: line-through;
  }
}
</style>
