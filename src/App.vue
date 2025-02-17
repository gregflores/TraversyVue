<script setup>
import { onMounted, ref } from 'vue';


const name = ref('Greg Flores')
const status = ref('active')
const tasks = ref(['Task 1', 'Task 2', 'Task 3', 'Task 4'])
const newTask = ref('');

const toggleStatus = () => {
  if (status.value === 'active') status.value = 'pending'
  else if (status.value === 'pending') status.value = 'inactive'
  else status.value = 'active'
}

const addTask = () => {
  if (newTask.value.trim() != '') {
    tasks.value.push(newTask.value);
    newTask.value = ''
  }
}

const deleteTask = (index) => {
  tasks.value.splice(index, 1)
}

onMounted(async () => {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/todos')
    const data = await response.json()
    tasks.value = data.map((task) => task.title);
  } catch (error) {
    console.log('Error fetching tasks')
  }
})
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is inactive</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" name="newTask" id="newTask" v-model="newTask">
    <button type="submit">Submit</button>
  </form>

  <h3>Tasks</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="index">
      <span>{{ task }}</span>
      <button @click="deleteTask(index)">X</button>
    </li>
  </ul>
  <a :href="link">Click me</a>

  <button @click="toggleStatus">Change Status</button>
</template>

<style scoped>
h1 {
  color: red;
}
</style>