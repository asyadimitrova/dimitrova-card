<script setup lang="ts">
  import Close from "@/assets/svg/close.vue";

  defineProps<{
    isOpen: boolean;
  }>();

  const emit = defineEmits(["modal-close"]);
</script>

<template>
  <dialog>
    <div
      class="overlay"
      @click="emit('modal-close')"
      v-if="isOpen"
    ></div>

    <article
      class="modal"
      v-if="isOpen"
    >
      <Close
        class="modal-close"
        @click="emit('modal-close')"
      />

      <slot name="carousel-about"></slot>
    </article>
  </dialog>
</template>

<style scoped>
  .overlay {
    position: fixed;
    inset: 0;
    background-color: rgba(0, 0, 0, 0.5);
    z-index: 1;
  }

  .modal {
    position: absolute;
    inset: 0;

    width: 100%;
    height: fit-content;

    padding: 10px;
    z-index: 2;

    display: flex;
    flex-direction: column;
    align-items: end;
  }

  .modal-close {
    position: absolute;
    width: 25px;
    height: 25px;

    right: -11px;
    top: -11px;

    cursor: pointer;
  }
</style>
