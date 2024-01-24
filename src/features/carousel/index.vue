<script setup lang="ts">
  import { ref } from "vue";

  import "vue3-carousel/dist/carousel.css";
  import { Carousel, Slide, Navigation } from "vue3-carousel";

  import Slide1 from "@/assets/image/slide-1.png";
  import Slide2 from "@/assets/image/slide-2.png";
  import Slide3 from "@/assets/image/slide-3.png";
  import Slide4 from "@/assets/image/slide-4.png";
  import Slide5 from "@/assets/image/slide-5.jpg";
  import Slide6 from "@/assets/image/slide-6.jpeg";
  import Slide7 from "@/assets/image/slide-7.jpg";

  interface ISlide {
    id: number;
    slide: string;
  }

  const currentSlideId = ref<number>(0);

  const slides = ref<ISlide[]>([
    {
      id: 1,
      slide: Slide6,
    },
    {
      id: 2,
      slide: Slide1,
    },
    {
      id: 3,
      slide: Slide2,
    },
    {
      id: 4,
      slide: Slide3,
    },
    {
      id: 5,
      slide: Slide4,
    },
    {
      id: 6,
      slide: Slide5,
    },
    {
      id: 7,
      slide: Slide7,
    },
  ]);

  const breakpoints = {
    400: {
      itemsToShow: 1,
      wrapAround: true,
    },

    700: {
      itemsToShow: 2,
      wrapAround: true,
    },

    1024: {
      itemsToShow: 3.95,
      wrapAround: true,
    },
  };

  const slideTod = (value: number) => {
    if (value !== currentSlideId.value) {
      console.log("slide", value, "and", currentSlideId.value);
      currentSlideId.value = value;
    }
  };
</script>

<template>
  <Carousel
    class="carousel"
    :transition="500"
    v-model="currentSlideId"
    :breakpoints="breakpoints"
  >
    <slide
      v-for="slide in slides"
      :key="slide.id"
    >
      <div
        class="carousel__item"
        @click="slideTod(slide.id - 1)"
      >
        <img
          class="item__image"
          :src="slide.slide"
          alt="about"
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
