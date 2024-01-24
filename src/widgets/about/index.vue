<script setup lang="ts">
  import { Carousel } from "@/features/carousel";
</script>

<template>
  <section
    class="about"
    id="about"
  >
    <div class="about__carousel">
      <Carousel />
    </div>
  </section>
</template>

<style scoped>
  .about {
    width: 100%;
  }

  .about__carousel {
    padding: 50px 0;
  }
</style>
