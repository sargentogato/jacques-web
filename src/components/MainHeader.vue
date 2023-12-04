<template>
  <div class="header row d-flex">
    <h1 class="header__title col-12 text-center pt-3 px-2">{{ title }}</h1>
  </div>
</template>

<script setup>
defineProps({
  title: String,
});
</script>

<style lang="scss" scoped>
.row {
  margin: 0;
}
.header {
  &__title {
    color: white;
    font-size: $title-size-mobile;
    font-family: $title-fontFamily;

    text-shadow: $text-shadow;
    z-index: 1;
  }
}

@media (width > 767px) {
  .header {
    &__title {
      position: absolute;
      font-size: $title-size-lg;
    }
  }
}

@media (width > 1400px) {
  .header {
    &__title {
      font-size: $title-size-xl;
    }
  }
}
</style>
