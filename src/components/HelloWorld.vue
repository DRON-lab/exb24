<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      Для того чтобы получить больше информации о Vue.js, посетите
      <a href="https://vuejs.org" target="_blank">официальный сайт</a>.
    </p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
};
</script>

<style scoped>
.hello {
  text-align: center;
  margin-top: 60px;
}
h1 {
  font-weight: normal;
  font-size: 30px;
}
</style>
