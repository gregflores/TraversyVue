<script>
export default{
  data() {
    return {
      name: 'Greg Flores',
      status: 'active',
      tasks: ['1','2','3','4'],
      link: '#'
    }
  },
  methods: {
    toggleStatus() {
      if(this.status === 'active') this.status = 'pending'
      else if(this.status === 'pending') this.status = 'inactive'
      else if(this.status === 'inactive') this.status = 'active'
    }
  }
}
</script>
<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is inactive</p>

  <h3>Tasks</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="index">{{ task }}</li>
  </ul>
  <a :href="link">Click me</a>

  <button @click="toggleStatus">Change Status</button>
</template>

<style scoped>
h1 {
  color: red;
}
</style>