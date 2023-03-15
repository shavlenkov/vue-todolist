<template>
  <input v-model="text" type="text">
  <button @click="createTask">Create</button>


  <div class="task" v-for="task in tasks" v-bind:key="task">
    <b>{{ task.text }}</b>

    <p class="cross" @click="deleteTask(task.id)">&#9746;</p>
  </div>
</template>

<script>

export default {
  name: 'App',

  data() {
    return {
      text: "",
      tasks: [
        {id: 1, text: "Hello, world"},
        {id: 2, text: "Hello, world"},
        {id: 3, text: "Hello, world"}
      ]
    }
  },

  methods: {
    createTask() {
      let newTask = {
        id: Date.now(),
        text: this.text
      }

      this.tasks.push(newTask);

      this.text = ''

    },


    deleteTask(id) {
      for(let i = 0; i < this.tasks.length; i++) {
        if(id == this.tasks[i].id) {
          this.tasks.splice(i, 1)
        }
      }
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

.task {
  display:flex;
  justify-content: space-between;
  align-items: center;
  border: 5px solid #000;
  padding: 10px;
  font-size: 30px;
  width: 50%;
  margin: 0 auto;
  margin-bottom: 20px;
}

input {
  width: 40%;
  height: 30px;
  margin-bottom: 20px;
}

button {
  width: 100px;
  height: 31px;
}

.cross {
  color: red;
}

</style>
