<script setup>
  import { ref, computed } from "vue"
  import { useRoute } from "vue-router"
  import quizes from "../data/quizes.json"
  import Question from "../components/Question.vue"

  const route = useRoute()
  const subjectID = parseInt(route.params.id)
  const quiz = quizes.find(quiz => quiz.id === subjectID)
  const currentQuestionIndex = ref(0)
  const correctAnswers = ref(0)

  const questionStatus = computed(() => `${currentQuestionIndex.value}/${quiz.questions.length}`)
  const completion = computed(() => `${currentQuestionIndex.value/quiz.questions.length * 100}%`)

  const onOptionSelected = (isTrue) => {
    if(isTrue) {
      correctAnswers.value++
    }
    currentQuestionIndex.value++
  }
</script>
<template>
  <div>
    <header>
      <!-- <pre>{{ quiz.questions }}</pre> -->
      <h1 class="title">{{ quiz.subject }}</h1>
      <div class="status">{{ questionStatus }}</div>
    </header>
    <div class="bar">
      <div class="completion" :style="{width: completion}"></div>
    </div>
    <div class="numbers">{{ completion }}</div>
    <div class="quiz">
      <Question
        :question="quiz.questions[currentQuestionIndex]"
        @selectOption="onOptionSelected"
      />
    </div>
  </div>
</template>

<style lang="scss" scoped>
  header {
    margin: 20px 0 15px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    .title {
      color: #777;
      font-size: 28px;
    }
    .status {
      color: #777;
    }
  }
  .bar {
    width: 100%;
    height: 8px;
    border: 1px solid #d7d7d7;
    border-radius: 10px;
    .completion {
      background: rgb(13, 212, 212);
      width: 0;
      height: 100%;
      border-radius: 10px;
    }
  }
  .numbers {
    color: #999;
    font-size: 12px;
  }
</style>
