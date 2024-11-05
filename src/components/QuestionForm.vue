<template>
  <div class="question">
    <p>{{ question.text }}</p>
    <div v-if="question.type === 'rating'">
      <input type="number" v-model="answer" min="1" max="5" placeholder="Оцените от 1 до 5" />
    </div>
    <div v-if="question.type === 'text'">
      <textarea v-model="answer" placeholder="Ваш ответ"></textarea>
    </div>
  </div>
</template>

<script>
export default {
  props: ['question'],
  data() {
    return {
      answer: ''
    };
  },
  watch: {
    answer(newValue) {
      this.$emit('input', newValue);
    }
  }
};
</script>

<style scoped>
.question {
  margin-bottom: 20px;
}
textarea {
  width: 100%;
  height: 100px;
}
input[type="number"] {
  width: 100%;
}
</style>
