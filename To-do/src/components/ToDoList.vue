
<template>
    <div>
      <h1>To-Do List</h1>
      <input v-model="newTask" @keyup.enter="addTask" placeholder="Add a new task" />
      <button @click="addTask">Add Task</button>
      
      <ul>
        <li v-for="(task, index) in tasks" :key="index">
          <input type="checkbox" v-model="task.completed" />
          <span :class="{ completed: task.completed }">{{ task.text }}</span>
          <button @click="removeTask(index)">Remove</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const newTask = ref('');
  const tasks = ref([
    { text: 'Learn Vue.js', completed: false },
    { text: 'Build a to-do list app', completed: false }
  ]);
  
  const addTask = () => {
    if (newTask.value.trim() !== '') {
      tasks.value.push({ text: newTask.value, completed: false });
      newTask.value = '';
    }
  };
  
  const removeTask = (index) => {
    tasks.value.splice(index, 1);
  };
  </script>
  
  <style scoped>
  div{
    text-align: center;
    justify-content: center;
  }
 /* .todo-container {
    display: flex;
  max-width: 600px;
  margin: 50px auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
} */

h1 {
  text-align: center;
  font-size: 24px;
  margin-bottom: 20px;
}

.input-container {
  text-align: center;
  display: flex;
  gap: 10px;
  margin-bottom: 20px;

}
input{
    width: 250px;
    height: 30px;
}

input[type="text"] {
  /* flex: 1; */
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  border: none;
  background-color: #42b983;
  color: white;
  cursor: pointer;
  border-radius: 4px;
  margin-left: 20px;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #369f6d;
}

ul {
  list-style-type: none;
  padding: 0;
}

.task-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 0;
  border-bottom: 1px solid #eee;
}

.task-item input[type="checkbox"] {
  margin-right: 10px;
}

.task-item span {
  flex: 1;
}

.task-item button {
  background-color: #e74c3c;
  padding: 5px 10px;
}

.task-item button:hover {
  background-color: #c0392b;
}

.completed {
  text-decoration: line-through;
  color: #aaa;
}
  </style>
  