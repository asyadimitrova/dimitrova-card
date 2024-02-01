<script setup lang="ts">
  import { ref } from "vue";

  import { Card } from "@/shared/card";
  import { Modal } from "@/features/modal";
  import { Carousel } from "@/features/carousel";

  import About from "@/assets/image/about.jpg";
  import About1 from "@/assets/image/about-1.jpg";

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

  const isModalOpened = ref<boolean>(false);
  const currentSlide = ref<number>();
  const modalSlide = ref<ISlide | undefined>();

  const handleOpenModal = (slideId: number) => {
    const findSlide = slides.value.find(e => e.id === slideId);
    modalSlide.value = findSlide;
    isModalOpened.value = true;
  };

  const handleCloseModal = () => {
    isModalOpened.value = false;
  };
</script>

<template>
  <section
    class="about"
    id="about"
  >
    <div class="about__me-desktop">
      <div class="about__card">
        <Card>
          <h1>Про мене</h1>
          <br />
          <p>
            До психології я прийшла через особисту терапію 5 років тому, яка продовжується по сьогоднішній день. Я
            являюсь дипломованим психологом, гештальт-консультантом й надалі продовжую своє навчання, адже психологія це
            про постійне вдосконалення знань та навичок на протязі всього життя.
          </p>
          <p>
            Мені відгукується робота з кожною окремою людиною як із індивідуальністю. Наша психіка утворена абсолютно
            унікальним, неповторним чином. Тож, у своїй практиці я використовую інтегративний підхід, залучаю всі
            накопичені знання з гештальт підходу, поведінкової терапії, психосоматики та психоаналізу, виходячи з запиту
            клієнта. Не існує одного підходу в психології на всі випадки життя, з кожною людиною процес йде неповторно,
            тож і методи обираються виходячи з запиту.
          </p>
          <p>
            Не існує одного підходу в психології на всі випадки життя, з кожною людиною процес йде неповторно, тож і
            методи обираються виходячи з запиту.
          </p>
        </Card>
      </div>

      <div class="about__image">
        <img
          :src="About"
          alt="about"
          class="image"
          loading="lazy"
        />
      </div>
    </div>

    <div class="about__me-mobile">
      <div class="test-class">
        <div class="about__card">
          <p>
            До психології я прийшла через особисту терапію 5 років тому, яка продовжується по сьогоднішній день. Я
            являюсь дипломованим психологом, гештальт-консультантом й надалі продовжую своє навчання, адже психологія це
            про постійне вдосконалення знань та навичок на протязі всього життя.
          </p>
        </div>

        <div class="about__image">
          <img
            :src="About"
            alt="about"
            class="image"
            loading="lazy"
          />
        </div>
      </div>

      <div class="test-class">
        <div class="about__image">
          <img
            :src="About1"
            alt="about"
            class="image"
            loading="lazy"
          />
        </div>
        <div class="about__card">
          <p>
            Мені відгукується робота з кожною окремою людиною як із індивідуальністю. Наша психіка утворена абсолютно
            унікальним, неповторним чином. Тож, у своїй практиці я використовую інтегративний підхід, залучаю всі
            накопичені знання з гештальт підходу, поведінкової терапії, психосоматики та психоаналізу, виходячи з запиту
            клієнта. Не існує одного підходу в психології на всі випадки життя, з кожною людиною процес йде неповторно,
            тож і методи обираються виходячи з запиту.
          </p>
        </div>
      </div>
    </div>

    <div class="about__carousel">
      <Carousel
        :slides="slides"
        :currentSlide="currentSlide"
        @modal-open="handleOpenModal"
      />
      <Modal
        :isOpen="isModalOpened"
        @modal-close="handleCloseModal"
      >
        <template #carousel-about>
          <img
            :src="modalSlide?.slide"
            alt="modal-image"
            class="about__carousel-image"
          />
        </template>
      </Modal>
    </div>
  </section>
</template>

<style scoped>
  .about {
    width: 100%;

    display: flex;
    flex-direction: column;
    gap: 25px;

    padding: 30px;
  }

  .about__me-desktop {
    width: 100%;

    display: flex;
    justify-content: space-between;
  }

  .about__me-mobile {
    display: none;
  }

  .about__card {
    width: 1000px;
  }

  h1 {
    font-family: "Cinzel Decorative", serif;
  }

  p {
    font-size: 18px;
    text-indent: 5%;
  }

  .image {
    width: 550px;
    height: 100%;

    object-fit: cover;
  }

  .about__carousel {
    position: relative;
  }

  .about__carousel-image {
    width: 100%;
    object-fit: fill;
  }

  @media screen and (max-width: 600px) {
    .test-class {
      /* border: 2px dotted blue; */
      /* padding: 10px; */
      /* height: 300px; */
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
    }
    .about {
      padding: 10px;
      gap: 5px;
    }
    .about__me-desktop {
      display: none;
    }

    .about__me-mobile {
      /* border: 2px solid red; */
      /* padding: 15px; */

      display: flex;
      flex-direction: column;
      justify-content: center;
      gap: 10px;
    }

    .about__image {
      width: 300px;
    }

    .image {
      width: 100%;
      height: 100%;

      object-fit: cover;
    }

    .about__card {
      /* background-color: red; */
      width: fit-content;
    }

    p {
      font-size: 12px;
      line-height: 18px;
      text-indent: 0%;
    }
  }
</style>
