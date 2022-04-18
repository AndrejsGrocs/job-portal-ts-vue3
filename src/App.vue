<template>
  <div class="app">
    <p>{{name}} - {{age}}</p>
    <button @click='changeName("Taschibana Ukyo")'>change name</button>
    <button @click='changeAge(31)'>change age</button>


  </div>
</template>

<script lang="ts">

let age1: string | number = 45   // We are not able to use it inside the data() object

import { defineComponent, reactive, toRefs } from "vue";

export default defineComponent({
  name: "App",
  components: {},
  setup(){
    const state = reactive({
      name: 'Link',
      age: 18 as string | number
    })
    return{...toRefs(state)}


  },
/*   data(){
    return{
      name:'Link',
      age: 25 as number | string     // The way how we choose type of data in objects and in this case data() object
    }
  }, */
  methods:{
    changeName(name: string){
       this.name =  name
       return name
    },
    changeAge(age: string|number){
      this.age = age
       return age                            // Ts automatically returns :void but if we will make a return then we will receive the information about returning data tye on hovering on the function name.
    }

  }
});
</script>

<style></style>
