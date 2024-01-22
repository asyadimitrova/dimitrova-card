<script setup lang="ts">
  import { reactive } from "vue";
  import Burger from "@/assets/svg/burger.vue";

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
  <nav class="navigation">
    <router-link
      v-for="item in navigation"
      :to="item.link"
    >
      {{ item.title }}
    </router-link>
  </nav>

  <div
    @click="toggleSidebarMobile"
    class="navigation-burger"
    v-if="!isVisibleSidebarMobile"
  >
    <Burger />
  </div>
</template>

<style scoped>
  .navigation {
    position: absolute;
    width: 100%;

    display: flex;
    justify-content: flex-end;
    text-align: center;
    gap: 80px;

    padding: 20px 50px 0px 0px;

    user-select: none;
  }

  .navigation-burger {
    display: none;
  }

  @media screen and (max-width: 845px) {
    .navigation-burger {
      display: flex;
      position: absolute;
      top: 20px;
      right: 30px;
    }

    .navigation {
      display: none;
    }
  }
</style>
