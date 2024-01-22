<script setup lang="ts">
  import { Header } from "@/widgets/header";
  import { ScrollButtonToTop } from "@/features/scroll-button-to-top";
</script>

<template>
  <Header />
  <div
    id="about"
    class="block"
  >
    <h1>About</h1>
  </div>
  <div
    id="contact"
    class="block"
  >
    <h1>Contact</h1>
  </div>
  <div
    id="review"
    class="block"
  >
    <h1>Review</h1>
  </div>
  <div
    id="faq"
    class="block"
  >
    <h1>FAQ</h1>
  </div>
  <ScrollButtonToTop />
</template>

<style scoped>
  .block {
    height: 500px;
  }
</style>
@/features/scroll-button-to-top
