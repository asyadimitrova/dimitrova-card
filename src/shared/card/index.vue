<template>
  <div class="card">
    <slot />
  </div>
</template>

<style scoped>
  .card {
    width: 100%;

    display: flex;
    flex-direction: column;
    gap: 10px;

    padding: 105px 96px;
    background-color: rgba(224, 216, 200, 0.3);
  }

  @media screen and (max-width: 600px) {
    .card {
      padding: 5px;
      height: -webkit-fill-available;
    }
  }
</style>
