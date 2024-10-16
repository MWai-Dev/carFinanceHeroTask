<script setup>
  import { ref } from 'vue';
  import HeroSection from './components/HeroSection.vue';
  import ApplicationForm from './components/ApplicationForm.vue';

  // Set changing values
  let loanValueCheck = ref(false);    
  let formSubmitted = ref(false);
  let chosenTerm = ref(6);
  let loanValue = ref(5000);

</script>

<template>

  <main>

    <HeroSection v-if="formSubmitted === false"
      v-model:loanValueCheck = "loanValueCheck"
      v-model:submitChange = "formSubmitted"
      v-model:chosenTerm = "chosenTerm"
      v-model:loanValue = "loanValue"
    />

    <ApplicationForm v-else="formSubmitted === true" 
      v-model:chosenTerm = "chosenTerm"
      v-model:loanValue = "loanValue"
    />

  </main>

</template>