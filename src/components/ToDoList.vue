<template>
    <div class="todo-container">
      <h1>To-Do List</h1>
  
      <div class="input-group">
        <input v-model="newTask" placeholder="Add a new task..." @keyup.enter="addTask" />
        <button @click="addTask">Add Task</button>
      </div>
  
      <ul class="task-list">
        <li v-for="(task, index) in tasks" :key="index">
          <div v-if="task.isEditing">
            <input type="text" v-model="task.text" />
            <button @click="saveTask(index)">Save</button>
          </div>
          <div v-else>
            <span>{{ task.text }}</span>
            <button @click="editTask(index)">Edit</button>
            <button @click="removeTask(index)">Delete</button>
          </div>
        </li>
      </ul>
  
      <div v-if="tasks.length > 0" class="footer">
        <p>{{ tasks.length }} tasks in total</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTask: '',
        tasks: []
      };
    },
    methods: {
      addTask() {
        if (this.newTask.trim()) {
          this.tasks.push({ text: this.newTask.trim(), isEditing: false });
          this.newTask = ''; 
        }
      },
      editTask(index) {
        this.tasks[index].isEditing = true;
      },
      saveTask(index) {
        if (this.tasks[index].text.trim()) {
          this.tasks[index].isEditing = false;
        }
      },
      removeTask(index) {
        this.tasks.splice(index, 1);
      }
    }
  };
  </script>
  
  <style scoped>
  .todo-container {
    max-width: 200%;
    margin: 0px auto;
    padding: 100px;
    background-color: #f9f9f9;
    border-radius: 50px;
    box-shadow: 25px 19px 10px rgba(0, 0, 0, 0.1);
    border: 2px solid;
  }
  
  .input-group {
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
  }
  
  .input-group input {
    flex: 1;
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  
  .input-group button {
    padding: 10px 15px;
    margin-left: 10px;
    background-color: #42b983;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  .input-group button:hover {
    background-color: #38a171;
  }
  
  .task-list {
    list-style: none;
    padding: 0;
    width: 120%;
  }
  
  .task-list li {
    display: flex;
    justify-content: space-between;
    padding: 12px;
    background-color: #fff;
    border-bottom: 1px solid #eee;
    margin-bottom: 10px;
    max-width: 100%;
    border-radius: 10px;
    margin-left: -25px;
  }
  
  .task-list button {
    margin-left: 10px;
    padding: 5px 10px;
    background-color: #e74c3c;
    color: white;
    border: none;
    border-radius: 3px;
    cursor: pointer;
  }
  
  .task-list button:first-of-type {
    background-color: #3498db;
  }
  
  .task-list button:hover {
    background-color: #c0392b;
  }
  
  .task-list button:first-of-type:hover {
    background-color: #2980b9;
  }
  
  .footer {
    margin-top: 20px;
    text-align: center;
  }
  </style>
  