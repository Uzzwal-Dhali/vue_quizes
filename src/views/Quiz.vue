<script setup>

</script>
<template>
  <div>
    <header>
      <h4>Question</h4>

    </header>
    <div class="bar">
        <div class="completion"></div>
      </div>
  </div>
</template>

<style lang="scss" scoped>
  header {
    margin: 20px 0 15px;
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
    }
  }
</style>
