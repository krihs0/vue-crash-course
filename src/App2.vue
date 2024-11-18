<script>
  export default {
    name: 'App2',
    data() {
      return {
        title: 'Kristick Jobs',
        status: 'active',
        jobs: ['developer', 'designer', 'manager'],
        link: 'https://krisockers.nl'
      }
    },
    methods: {
      toggleStatus() {
        this.status = this.status === 'active' ? 'pending' : 'active';
      }
    }
  }
</script>

<template>
    <h1>{{ title }}</h1>
    <h2 v-if="status === 'active'">Welcome to Kristick Jobs</h2>
    <h2 v-else-if="status === 'pending'">Kristick Jobs is under review</h2>
    <h2 v-else>Sorry, Kristick Jobs is not available</h2>

    <h3>Jobs</h3>
    <ul>
      <li v-for="job in jobs" :key="job">{{ job }}</li>
    </ul>

    <a :href="link">Visit Kristicks</a>

    <button v-on:click="toggleStatus">Change status</button>
</template>

<style scoped>
  h1 {
    color: #333;
    font-size: 2em;
    text-align: center;
    margin-top: 20px;
  }
</style>