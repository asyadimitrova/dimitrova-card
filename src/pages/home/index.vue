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
    2. Need to fixes adaptive mobile 

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
    <!-- example accordion html first-->
    <!-- <section role="group">
      <details name="accordion">
        <summary>one</summary>
        <span>
          Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aspernatur modi distinctio expedita aperiam itaque
          maxime culpa enim ducimus porro fugiat assumenda qui facilis velit, quo et facere, similique iusto
          exercitationem.
        </span>
      </details>

      <details name="accordion">
        <summary>two</summary>
        <span>
          Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aspernatur modi distinctio expedita aperiam itaque
          maxime culpa enim ducimus porro fugiat assumenda qui facilis velit, quo et facere, similique iusto
          exercitationem.
        </span>
      </details>
    </section> -->
  </div>
  <ScrollButtonToTop />
</template>

<style scoped>
  .horizontal-media-scroller {
    display: grid;
    grid-auto-flow: column;
    grid-gap: calc(var(--gap) / 2);

    overflow: auto;
    overscroll-behavior-x: contain;
    scroll-snap-type: x mandatory;
    scroll-padding-inline: var(--gap);
  }

  .horizontal-media-scroller figure {
    scroll-snap-align: start;
  }
  .block {
    height: 800px;
  }
</style>
