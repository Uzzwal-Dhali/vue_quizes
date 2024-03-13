<script setup>
  import { RouterLink } from "vue-router"
  const { subject } = defineProps([
    'subject'
  ])
</script>

<template>
  <div class="subject">
    <h1 class="title">{{ subject.subject }}</h1>
    <div class="questions">{{ subject.questions.length }} Questions</div>
  </div>
</template>

<style lang="scss" scoped>

.subject {
  padding: 15px;
  background: white;
  border-radius: 10px;
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

</style>
