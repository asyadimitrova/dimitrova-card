<script setup lang="ts">
  import { ref, onMounted, onBeforeUnmount } from "vue";
  import ChevronUp from "@/assets/svg/chevron-up.vue";

  const isVisibleButton = ref(false);

  const handleScrollY = () => {
    isVisibleButton.value = scrollY > 150;
  };

  onMounted(() => {
    window.addEventListener("scroll", handleScrollY);
  });

  onBeforeUnmount(() => {
    window.removeEventListener("scroll", handleScrollY);
  });
</script>

<template>
  <router-link
    to="#main"
    class="button-up"
    v-if="isVisibleButton"
  >
    <ChevronUp />
  </router-link>
</template>

<style scoped>
  .button-up {
    display: flex;
    position: fixed;
    bottom: 20px;
    right: 20px;
    padding: 10px;

    border-radius: 5px;
    font-size: 16px;

    background-color: #dddfe2;
    color: #fff;
    cursor: pointer;
  }
</style>
