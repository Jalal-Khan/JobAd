

<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="site logo">
        <h1>ByteCraft Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('location')">order by location</button>
        <button @click="handleClick('salary')">order by salary</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order"/>
    <footer>
    <p>Made with love by ByteCraft</p>
  </footer>
  </div>

</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import JobList from './components/JobList.vue';
import { type Job } from './interfaces/jon';
import type { OrderTerm } from './interfaces/OrderTerm';

export default defineComponent({
  name: 'App',
  components: { JobList }, 
  setup(){

    const jobs = ref<Job[]>([
      {id: 1, title: 'JS Developer', description: 'Seeking skilled JavaScript Developer to design, develop, and implement innovative web applications, ensuring seamless user experiences and robust functionality in a dynamic and collaborative team environment.', location: 'London', company: 'Meta', salary: 250},
      {id: 2, title: 'Node Developer', description: 'Passionate Node.js Developer with expertise in building scalable and efficient server-side applications, utilizing cutting-edge technologies to deliver robust and high-performance solutions.', location: 'Islamabad', company: 'Techchaps', salary: 200},
      {id: 3, title: 'Database Expert', description: 'Experienced Database Expert Unlocking the power of data through advanced database management, optimization, and seamless integration to drive efficiency and innovation.', location: 'Istanbul', company: 'Google', salary: 180},
      {id: 4, title: 'DotNet Developer', description: 'Seeking skilled and motivated DotNet Developer to contribute to the development and enhancement of robust, scalable, and innovative software solutions within a dynamic team environment.', location: 'NewYork', company: 'PacSquare', salary: 150},  
      {id: 5, title: 'Swift Developer', description: 'Exciting opportunity for a skilled Swift developer to join our dynamic team, contributing to the development of cutting-edge iOS applications with a focus on innovation and user experience.', location: 'Peshawar', company: 'Apple', salary: 240},
    ])

    const order = ref<OrderTerm>('title')
    const handleClick=(term: OrderTerm)=>{
      order.value=term;
    };

    return {
      jobs,
      handleClick,
      order
    }
  }
});
</script>

<style scoped>
  
  header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  button {
    margin: 0 10px;
    /* color: #1195c9; */
    border: 3px solid linear-gradient(to right, #a3e3ff, #a3ffa3, #e6e6e6);
    /* background: #d5f0ff; */
    color: #17bf66; /* Text color when not hovered */
    background: #001F3F;
    padding: 8px 16px;
    border-radius: 4px;
    /* border-color: linear-gradient(to right, #a3e3ff, #a3ffa3, #e6e6e6); */
    cursor: pointer;
    font-weight: bold;
    transition: background 0.3s ease; /* Add a smooth transition effect */
  }
  button:hover {
    color: #001F3F;
  background: #17bf66; /* Change the background color on hover */
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
  footer {
  /* background-color: #001F3F; Adjust the background color as neede */
  color:#001F3F; /* Text color for the footer */
  text-align: center;
  padding: 10px;
  /* position: fixed; */
  display: flex;
  justify-content: center;
  align-items: center;
  align-self: center;
  bottom: 0;
  width: 100%;
  /* height: 30px; */
}
</style>
