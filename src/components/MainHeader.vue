<template>
  <div class="header row d-flex">
    <h1 class="header__title col-12 text-center pt-3 px-2">{{ title }}</h1>
    <div class="header__imagesBox">
      <picture
        class="imagesBox__picture"
        v-for="(imageText, index) in imageText"
        :key="index"
      >
        <source
          media="(min-width:0px)"
          :srcset="getImage(imageText.instrument)"
        />
        <img
          :src="getImage(imageText.instrument)"
          alt=""
          :style="{ animationDelay: `${index * 0.5}s` }"
          class="fade-in"
        />
      </picture>
    </div>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  imageText: Object,
});

function getImage(image) {
  const path = new URL("../../public/images", import.meta.url).href;

  return `${path}/${image}`;
}
</script>

<style lang="scss" scoped>
.row {
  margin: 0;
}
.header {
  height: 250px;
  background-color: black;

  &__title {
    color: white;
    font-size: $title-size-mobile;
    font-family: $title-fontFamily;

    text-shadow: $text-shadow;
  }

  &__imagesBox {
    height: 250px;
    overflow: hidden;
    display: flex;
    padding-top: 1rem;
    padding-bottom: 2rem;

    img {
      width: 100%;
      height: 50%;
      object-fit: contain;
    }
  }
}

.fade-in {
  opacity: 0;
  animation: fadeIn 1s forwards;
}

@keyframes fadeIn {
  to {
    opacity: 1;
  }
}

@media (width > 767px) {
  .header {
    height: initial;

    &__title {
      position: absolute;
      font-size: $title-size-lg;
      z-index: 1;
    }

    &__imagesBox {
      display: none;
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
