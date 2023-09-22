<script setup lang="ts">
// import SpecialUploader from "./components/special-uploader.vue"
const url = "https://source.unsplash.com/random";
</script>

<template>
  <header>
    <div class="wrapper">
      <h3>hi</h3>
      <special-uploader :custom-img="url" />
    </div>
  </header>
</template>

<style scoped>
</style>
