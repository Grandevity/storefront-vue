<template>
    <LoginCard/>
  </template>
  
  <script>
  import { defineComponent } from 'vue';
  
  // Components
  import LoginCard from '../components/loginCard.vue';
  
  export default defineComponent({
    name: 'LoginView',
  
    components: {
        LoginCard,
    },
  });
  </script>
  