<template>
  <div id="app">
    <SurveyForm />
  </div>
</template>

<script>
import SurveyForm from './components/SurveyForm.vue'; // Убедитесь, что путь правильный
/* eslint-disable no-unused-vars */
import axios from 'axios';
/* eslint-enable no-unused-vars */

export default {
  components: {
    SurveyForm
  }
};
</script>