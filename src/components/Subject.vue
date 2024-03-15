<script setup>
  import { useRouter } from "vue-router"
  const router = useRouter()

  const { subject } = defineProps([
    'subject'
  ])

  const navigateToQuiz = () => {
    router.push(`/quiz/${subject.id}`)
  }
</script>

<template>
  <div @click="navigateToQuiz" class="subject">
    <h1 class="title">{{ subject.subject }}</h1>
    <div class="questions">{{ subject.questions.length }} Questions</div>
  </div>
</template>

<style lang="scss" scoped>

.subject {
  padding: 15px;
  background: white;
  border-radius: 10px;
  transition: all 0.3s ease-in-out;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
  cursor: pointer;
  .title {
    font-size: 18px;
    color: #7c7c7c;
    font-weight: 400;
  }
  .questions {
    color: #888;
    font-size: 13px;
  }
}

.subject:hover {
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}
</style>
