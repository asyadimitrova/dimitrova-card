<script setup lang="ts">
  import { reactive } from "vue";

  import Close from "@/assets/svg/close.vue";

  defineProps<{
    toggleSidebarMobile: () => void;
    isVisibleSidebarMobile: boolean;
  }>();

  interface INav {
    link: string;
    title: string;
  }

  const navigation = reactive<INav[]>([
    {
      link: "#about",
      title: "про мене",
    },
    {
      link: "#contact",
      title: "запис на консультацію",
    },
    {
      link: "#review",
      title: "відгуки",
    },
    {
      link: "#faq",
      title: "часті запитання ",
    },
  ]);
</script>

<template>
  <nav class="navigation-mobile">
    <router-link
      v-for="item in navigation"
      :to="item.link"
      @click="toggleSidebarMobile"
    >
      {{ item.title }}
    </router-link>
  </nav>
  <div
    @click="toggleSidebarMobile"
    class="navigation-mobile__close"
  >
    <Close />
  </div>
</template>

<style scoped>
  .navigation-mobile,
  .navigation-mobile__close {
    display: none;
  }

  @media screen and (max-width: 845px) {
    .navigation-mobile {
      position: absolute;
      width: 100%;
      height: 100%;

      display: flex;
      flex-direction: column;
      justify-content: start;
      align-items: start;
      gap: 10px;
      padding: 40px;

      animation: 0.5s 1 forwards slideRight;
      transform: translateX(-100%);

      background-color: rgb(255, 255, 255, 0.5);
    }

    .navigation-mobile__close {
      position: absolute;
      display: flex;
      top: 20px;
      right: 30px;
    }
  }

  @keyframes slideRight {
    from {
      transform: translateX(100%);
    }
    to {
      transform: translateX(0);
    }
  }
</style>
