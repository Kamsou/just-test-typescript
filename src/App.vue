<template>
  <div class="app">
    <header>
      <div>
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>
    
    <JobsList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, } from 'vue';
import JobsList from './components/JobsList.vue'
import Job from './types/Job'
import OrderTerm from './types/OrderTerm'

export default defineComponent({
  name: 'App',
  components: { JobsList },
  setup() {


    const jobs = ref<Job[]>([
      { title: 'Développeur Front-End', location: 'Paris', salary: 60000, id: '1'},
      { title: 'Développeur Back-End', location: 'Marseille', salary: 50000, id: '2'},
      { title: 'Designer UI', location: 'Bordeaux', salary: 40000, id: '3'},
      { title: 'Designer UIX', location: 'Toulouse', salary: 40000, id: '4'},
      { title: 'Product Owner', location: 'Paris', salary: 55000, id: '5'},
    ])
    const order = ref<OrderTerm>('title')

    const handleClick = (term: OrderTerm) => {
      order.value = term
    }

    return { jobs, handleClick, order }
  },
});
</script>

<style>
  header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  button {
    margin: 0 10px;
    color: rgb(14, 14, 14);
    border: 1px solid rgb(14, 14, 14);
    background:  antiquewhite;
    padding: 12px 24px;
    cursor: pointer;
    font-weight: bold;

    
  }
  button:hover {
    background:  rgb(14, 14, 14);
    color: antiquewhite;

    transition: all .2s ease-in-out;
  }
  header .title{
    display: flex;
    justify-content: center;
  }
  header img {
    width: 60px;
    margin-right: 20px;
  }
  header h1 {
    font-size: 3em;
  }
</style>
