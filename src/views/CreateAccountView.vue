<template>
    <createAccountCard/>
  </template>
  
  <script>
  import { defineComponent } from 'vue';
  
  // Components
  import createAccountCard from '../components/createAccountCard.vue';
  
  export default defineComponent({
    name: 'CreateAccountView',
  
    components: {
        createAccountCard,
    },
  });
  </script>
  