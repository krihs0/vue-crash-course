<script setup>
  import { ref, onMounted } from 'vue';

  const title = ref('Kristick Jobs');
  const status = ref('active');
  const jobs = ref(['developer', 'designer', 'manager']);
  const newJob = ref('');

  const toggleStatus = () => {
    status.value = status.value === 'active' ? 'pending' : 'active';
  }
  const addJob = ( ) => {
   if(newJob.value.trim()){
      jobs.value.push(newJob.value);
      newJob.value = '';
    }
  }

  const deleteJob = (index) => {
    jobs.value.splice(index, 1); 
  }

  onMounted(async () => {
    try {
      const response = await fetch('https://jsonplaceholder.typicode.com/todos');
      const data = await response.json();
      jobs.value = data.map((item) => item.title);
    } catch (error) {
      console.log("Error fetching data: ", error);
    }
  });
</script>

<template>
  <div>
    <h1>{{ title }}</h1>
    <h2 v-if="status === 'active'">Welcome to Kristick Jobs</h2>
    <h2 v-else-if="status === 'pending'">Kristick Jobs is under review</h2>
    <h2 v-else>Sorry, Kristick Jobs is not available</h2>

    <form @submit.prevent="addJob">
      <label for="newJob">Add a new job</label>
      <input type="text"id="newJob" name="newJob" placeholder="Add a new job" v-model="newJob">
      <button type="submit">Add</button>
    </form>

    <h3>Jobs</h3>
    <ul>
      <li v-for="(job, index) in jobs" :key="index">
          <span>{{ job }}</span>
          <button @click="deleteJob(index)">x</button>
      </li>
    </ul>

    <button v-on:click="toggleStatus">Change status</button>
  </div>
</template>

<style scoped>
  h1 {
    color: #333;
    font-size: 2em;
    text-align: center;
    margin-top: 20px;
  }
</style>