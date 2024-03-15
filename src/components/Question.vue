<script setup>
  import { defineEmits } from 'vue';
  const question = defineProps([
    'question'
  ])

  const emit = defineEmits(["selectOption"])
  const emitSelectedOption = (isTrue) => {
    emit("selectOption", isTrue)
  }
</script>

<template>
  <h1 class="question">{{ question.question.body }}</h1>
  <div class="options">
    <div v-for="option in question.question.options" @click="emitSelectedOption(option.isTrue)" class="option">
      <div class="label">{{ option.label }}</div>
      <div class="answer">{{ option.answer }}</div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  .question {
    font-size: 16px;
    padding: 15px 0;
    font-weight: 100;
    color: #555;
  }
  .options {
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
    justify-content: center;
    .option {
      display: flex;
      gap: 0.125rem;
      transition: all 0.3s ease-in;
      .label {
        height: 28px;
        width: 28px;
        border: 1px solid #d7d7d7;
        border-radius: 50%;
        display: flex;
        justify-content: center;
        align-items: center;
        color: #888;
      }
      .answer {
        border: 1px solid #d7d7d7;
        width: 100%;
        border-radius: 10px;
        padding-left: 10px;
        display: flex;
        align-items: center;
        color: #888;
      }
    }
    :hover {
      cursor: pointer;
      .answer {
        background: rgba(24, 208, 182, 0.25);
      }
    }
  }
</style>
