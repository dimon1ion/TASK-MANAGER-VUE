<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <TaskManager/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TaskManager from './components/TaskManager.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    TaskManager
}
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.row {
  margin: 0 !important;
  > * {
    padding: 0;
  }
}
</style>
