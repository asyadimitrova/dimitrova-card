<script setup lang="ts">
  import { Header } from "@/widgets/header";
  import { About } from "@/widgets/about";

  import { ScrollButtonToTop } from "@/features/scroll-button-to-top";

  /*

    TODO:

    Widgets:
    1. About []
    2. Cntact []
    3. Review []

    Features:
    1. Modal []

    FIXES:

    1. Carousel -> returns to the beginning rather than continuing to switch slides

    */
</script>
<template>
  <Header />
  <About />

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
    height: 800px;
  }
</style>
