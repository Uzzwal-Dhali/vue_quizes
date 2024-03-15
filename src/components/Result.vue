<script setup>
  import { RouterLink } from 'vue-router';
  const { questionsLength, correctAnswers } = defineProps([
    'questionsLength', 'correctAnswers'
  ])
</script>

<template>
  <div class="results">
    <h1 class="message">Your score is {{ (correctAnswers/questionsLength).toFixed(4) * 100}}%</h1>
    <div class="score">
      {{ correctAnswers }}/{{ questionsLength }}
    </div>
    <RouterLink to="/">Back to HOME</RouterLink>
  </div>
</template>

<style lang="scss" scoped>
  .results {
    height: 80vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    .message {
      font-size: 18px;
      color: #999;
    }
    .score {
      font-size: 60px;
      color: #a5a5a5;
    }
    a {
      text-decoration: none;
      color: #a5a5a5;
      font-size: 13px;
      transition: color 0.3s easy-in;
    }
    a:hover {
      color: rgb(250, 113, 119);
    }
  }
</style>
