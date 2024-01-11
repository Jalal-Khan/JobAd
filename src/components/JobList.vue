<template>
    <div class="job-list">
        <p>Ordered by {{ order }}</p>
        <ul>
            <li v-for="job in orderedJobs" :key="job.id">
                <h2>{{ job.title }} in {{ job.location }}</h2>
                <div class="salary">
                    <img src="../assets/rupee.svg" alt="repee icon">
                    <p>{{ job.salary }}k rupees</p>
                </div>
                <p>{{ job.company }}</p>
                <div class="description">
                    <p>{{ job.description }}</p>
                </div>
            </li>
        </ul>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref, type Prop, type PropType, computed } from 'vue';
import { type Job } from '../interfaces/jon';
import type { OrderTerm } from '@/interfaces/OrderTerm';

export default defineComponent({
    props : {
        jobs: {
            type: Array as PropType<Job[]>,
            required: true
        },
        order: {
            type: String as PropType<OrderTerm>
        }
    },
    setup(props){
        const orderedJobs = computed(() => {
                if(props.order){

                    return [...props.jobs].sort((a:Job ,b: Job) => {
                        return a[props.order!] > b[props.order!] ? 1 : -1
                    
                    });
                }
                else{
                    return props.jobs;
                }
        });
        return {
            orderedJobs
        }

    }

});
</script>


<style scoped>
  .job-list {
    max-width: 960px;
    margin: 40px auto;
  }
  .job-list ul {
    padding: 0;

  }
  .job-list li {
    list-style-type: none;
    background: #0056ad;
    color: #E4E6E4;

    padding: 16px;
    margin: 16px 0;
    border-radius: 4px;
  }
  .job-list h2 {
    margin: 0 0 10px;
    text-transform: capitalize;
  }
  .salary {
    display: flex;
  }
  .salary img {
    width: 30px;
  }
  .salary p {
    color: #17bf66;
    font-weight: bold;
    margin: 10px 4px;
  }

</style>