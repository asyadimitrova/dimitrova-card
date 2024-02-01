<script setup lang="ts">
  import { ref } from "vue";

  import "vue3-carousel/dist/carousel.css";
  import { Carousel, Slide, Navigation } from "vue3-carousel";

  const emit = defineEmits(["modal-open"]);

  defineProps<{
    slides: {
      id: number;
      slide: string;
    }[];
  }>();

  const currentSlideId = ref<number>(0);
  const slideTo = (value: number) => {
    if (value !== currentSlideId.value) {
      currentSlideId.value = value;
    }
  };

  const breakpoints = {
    400: {
      itemsToShow: 1,
    },

    700: {
      itemsToShow: 2,
    },

    1024: {
      itemsToShow: 3.95,
    },
  };
</script>

<template>
  <Carousel
    class="carousel"
    :transition="500"
    v-model="currentSlideId"
    :breakpoints="breakpoints"
    :wrapAround="true"
  >
    <slide
      v-for="slide in slides"
      :key="slide.id"
    >
      <div
        class="carousel__item"
        @click="slideTo(slide.id - 1)"
      >
        <img
          class="item__image"
          :src="slide.slide"
          alt="about"
          @click="emit('modal-open', slide.id)"
          loading="lazy"
        />
      </div>
    </slide>

    <template #addons>
      <navigation />
    </template>
  </Carousel>
</template>

<style scoped>
  .carousel {
    width: 100%;
  }
  .carousel__item {
    height: 300px;
    width: 300px;

    display: flex;
    justify-content: center;
    align-items: center;

    cursor: pointer;
  }

  .item__image {
    object-fit: contain;
    width: 100%;
    height: 100%;
  }

  .carousel__slide {
    padding: 5px;
  }

  .carousel__track {
    transform-style: preserve-3d;
  }

  .carousel__slide--sliding {
    transition: 0.5s;
  }

  .carousel__slide--active ~ .carousel__slide {
    transform: rotateY(20deg) scale(0.9);
  }

  .carousel__slide--prev {
    opacity: 0.4;
    transform: rotateY(-10deg) scale(0.95);
  }

  .carousel__slide--next {
    opacity: 0.4;
    transform: rotateY(10deg) scale(0.95);
  }

  .carousel__slide--active {
    opacity: 1;
    transform: rotateY(0) scale(1.2);
  }
</style>
