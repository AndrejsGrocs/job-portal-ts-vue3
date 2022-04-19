<template>
   <div class="job-list">
     <p class="ordered">Ordered by {{order}}</p>
    <ul>
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
         <img src="https://wowslider.com/sliders/demo-1/data1/images/butterfly1.png" alt="">
          <p>{{ job.salary }} Euros</p>
        </div>
        <div class="description">
          <p class="text-block">Job description is that you are able to code, than you can choose your position and contact the employer, thay will reply to you and you will get an amzing job. Enjoy!</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType, computed } from 'vue'
import Job from "../types/Job"
import OrderTerm from '../types/OrderTerm'

export default defineComponent({
    props:{
       jobs: {
           required: true,
           type: Array as PropType<Job[]>
       },
       order:{
         required:true,
         type: String as PropType<OrderTerm>

       }


    },
   setup(props) {
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1
      })
    })
    return { orderedJobs }
    }
  
})
</script>


<style scoped>
  .job-list {
    max-width: 960px;
    margin: 40px auto;
  }
  .job-list ul {
    padding: 0
  }
  .job-list li {
    list-style-type: none;
    background: #2F9599 ;
    padding: 16px;
    margin: 16px 0;
    border-radius: 4px;
    border-radius: 30px;
  }
  .job-list h2 {
    margin: 0 0 10px;
    text-transform: capitalize;
    color: #000;
  }
/*     .job-list p {
    margin: 0 0 10px;
    text-transform: capitalize;
    color: #F26B38;
  } */
  .salary {
    display: flex;
  }
   
     .salary img {
    width: 100px;
  }
  .salary p {
    color: #F7DB4F;
    font-weight: bold;
    margin: 10px 4px;
  }
  .list-move {
    transition: all 1s;
  }
  .text-block{
    color: #000;
  }

  .ordered{
     margin: 0 0 10px;
    text-transform: capitalize;
    color: #F26B38;
  }
</style>