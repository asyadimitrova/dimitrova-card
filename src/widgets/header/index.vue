<script setup lang="ts">
  import { ref } from "vue";
  import { Navigation } from "@/features/navigation";
  import { NavigationMobile } from "@/features/navigation-mobile";

  import ImageHeaderMain from "@/assets/image/header-image-x.png";
  import ImageHeaderSecond from "@/assets/image/mobile-image-2.png";

  const isVisibleSidebarMobile = ref(false);
  const toggleSidebarMobile = () => {
    isVisibleSidebarMobile.value = !isVisibleSidebarMobile.value;
  };
</script>

<template>
  <header
    id="main"
    class="header"
  >
    <NavigationMobile
      v-if="isVisibleSidebarMobile"
      :toggleSidebarMobile="toggleSidebarMobile"
      :isVisibleSidebarMobile="isVisibleSidebarMobile"
    />
    <Navigation
      :toggleSidebarMobile="toggleSidebarMobile"
      :isVisibleSidebarMobile="isVisibleSidebarMobile"
    />
    <picture>
      <source
        class="header__background"
        :srcset="ImageHeaderSecond"
        media="(max-width: 767px)"
      />
      <source
        class="header__background"
        :srcset="ImageHeaderSecond"
        media="(max-width: 1207px)"
      />
      <img
        class="header__background"
        :src="ImageHeaderMain"
        alt="header"
      />
    </picture>
  </header>
</template>

<style scoped>
  .header {
    width: 100%;
    height: 100svh;
  }

  .header__background {
    object-fit: cover;
    inset: 0;
    width: 100%;
    height: 100%;
  }
</style>
