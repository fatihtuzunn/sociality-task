<template>
  
  <TaskHome />
</template>

<script>
import TaskHome from './views/TaskHome.vue'

export default {
  name: 'App',
  components: {
    TaskHome
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: black;
  
}
</style>
