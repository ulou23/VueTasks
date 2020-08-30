<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h4 class="bg-secondary text-white text-center p-2"> {{name}} Tasks List </h4>
  <div class="container-fluid p-4">
    <div class="row" v-if="filteredTasks.length == 0">
      <div class="col text-center">
        <b> Nothing to do.</b>
      </div>
    </div>
    <template v-else>
      <div class="row">
        <div class="col font-weight-bold">TASK</div>
      <div class="col-2 font-weight-bold">Done</div>
    </div>
      <div class="row" v-for="task in filteredTasks" v-bind:key="task.action">
  <div class="col">{{task.action}} </div>
      <div class="col-2 text-center">
        <input type="checkbox" v-model="task.done" class="form-check-input"/>
  </div>
    </div>
    </template>
    <div class="row py-2">
      <div class="col">
        <input v-model="newItem" class="form-control" />
      </div>
      <div class="col-sm-4">
        <button class="btn btn-secondary" v-on:click="addNew">Add Task</button>
      </div>
    </div>
    <div class="row bg-secondary py-2 mt-2 text-white">
      <div class="col text-center">
        <input class="form-check-inline" type="checkbox" v-model="hideCompleted" />
        <label class="form-check-inline font-weight-bold">
          Hide completed tasks please
        </label>
      </div>
      <div class="col text-center">
        <button class="btn btn-sm btn-danger" v-on:click="deleteCompleted"> Delete completed forever</button>
      </div>
    </div>
  </div>
  </div>
</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      name: "Alan",
      tasks:[],
      hideCompleted:true,
      newItem:""
    }
  },
  computed: {
    filteredTasks(){
      return this.hideCompleted ? this.tasks.filter(task=>!task.done): this.tasks
    }
  },
  methods: {
    addNew(){
      this.tasks.push({
        action: this.newItem,
        done: false
      });
      this.storeData();
      this.newItem="";
    },
    storeData(){
      localStorage.setItem("listasks", JSON.stringify(this.tasks));
    },
    deleteCompleted(){
      this.tasks=this.tasks.filter(task=>!task.done);
      this.storeData();
    }
  },
  created(){
    let data=localStorage.getItem("listasks");
    if (data!=null){
      this.tasks=JSON.parse(data)
    }
  }
}
</script>

<style>
#app {

  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}
</style>
