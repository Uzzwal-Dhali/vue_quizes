<script setup>
  import quizes from '../data/quizes.json'
  import { ref, watch } from 'vue'
  import Subject from '../components/Subject.vue'

  const subjects = ref(quizes)
  const search = ref("")

  watch(search, () => {
    subjects.value = quizes.filter(quiz => quiz.subject.toLowerCase().includes(search.value.toLowerCase()))
  })
</script>

<template>
  <div>
    <div class="header">
      <div class="title">QUIZ APP</div>
      <div class="search">
        <input v-model.trim="search" type="text" placeholder="Search Here">
      </div>
    </div>
    <div class="subjects">
      <Subject v-for="subject in subjects" :key="subject.id" :subject="subject"/>
    </div>
  </div>
</template>

<style lang="scss">

    .header {
      margin-bottom: 20px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      .title {
        color: #757575;
        font-size: 22px;
      }
      .search {
        input {
          border: 1px solid #d7d7d7;
          border-radius: 5px;
          padding: 7px 10px;
          box-shadow: none;
          outline: none;
          color: #757575;
        }
      }
    }
    .subjects {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 10px;
    }
</style>
