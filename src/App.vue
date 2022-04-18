<template>
  <div class="app">
   <!--  <p>{{name}} - {{age}}</p>
    <button @click='changeName("Taschibana Ukyo")'>change name</button>
    <button @click='changeAge(31)'>change age</button> -->


     <JobList :jobs="jobs"/>


  </div>
</template>

<script lang="ts">

let age1: string | number = 45   // We are not able to use it inside the data() object

import { defineComponent, reactive, ref, toRefs } from "vue";
import JobList from './components/JobList.vue'
import Job from './types/Job'

export default defineComponent({
  name: "App",
  components: {JobList},
  setup(){   
    //Way how to use reactive()

/*     const state = reactive({
      name: 'Link',
      age: 18 as string | number
    })

     state.name = 'Hatori Hanzo'  // cannot change type here we are not able to use number or any other type.

    return{...toRefs(state)} */

     // way to use Refs

/*      const name = ref('Link')
     const age =ref<string | number>(25)  // The way hoe to use generics in refs, ref <string | number>(25)

     return {name, age} */

    const jobs = ref<Job[]>([

            {title: 'farm worker', location: 'Munich', salary: 100000, id:'1' }, 
            {title: 'web developer', location: 'Berlin', salary: 100000, id:'1' }, 
            {title: 'game stester', location: 'Hamburg', salary: 100000, id:'1' }, 
            {title: 'react developer', location: 'Regensburg', salary: 100000, id:'1' }, 

     ]) 
     return {jobs}
   
      
  },
/*   data(){
    return{
      name:'Link',
      age: 25 as number | string     // The way how we choose type of data in objects and in this case data() object
    }
  }, */





/*   methods:{
    changeName(name: string){
       this.name =  name
       return name
    },
    changeAge(age: string|number){
      this.age = age
       return age                            // Ts automatically returns :void but if we will make a return then we will receive the information about returning data tye on hovering on the function name.
    }

  } */
});
</script>

<style></style>
