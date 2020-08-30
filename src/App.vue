<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h4 class="bg-secondary text-white text-center p-2">
    {{name}} Tasks List </h4>
  </div>
  <div class="container-fluid p-4">
    <div class="row" v-if="filteredTasks.length==0">
      <div class="col text-center">
        <b> Nothing to do.</b>
      </div>
    </div>
    <template v-else>
      <div class="row">
        <div class="col font-weight-bold"
      </div>
    </template>
  </div>
</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      name: "Alana"
    }
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
  margin-top: 60px;
}
</style>
