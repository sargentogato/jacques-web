<template>
  <section class="row">
    <div
      class="imageBox col-12 col-md gap-0 p-0"
      :class="imageText.lineOne"
      v-for="imageText in props.imageText"
    >
      <picture class="imageBox__picture">
        <source
          media="(min-width:768px)"
          :srcset="getImage(imageText.desktop)"
        />
        <source media="(min-width:0px)" :srcset="getImage(imageText.mobile)" />
        <img :src="getImage(imageText.desktop)" alt="" />
      </picture>

      <a
        @click="addModal(imageText.lineOne)"
        class="imageBox__link"
        :class="imageText.lineOne"
      >
        <p class="imageBox__text mb-0">{{ imageText.lineOne }}</p>
        <p class="imageBox__text mb-0">{{ imageText.lineTwo }}</p>
      </a>
    </div>
  </section>
</template>

<script setup>
const props = defineProps(["imageText"]);
const emit = defineEmits(["addModal"]);

function getImage(image) {
  const path = new URL("../../public/images", import.meta.url).href;

  return `${path}/${image}`;
}

function addModal(event) {
  emit("addModal", event);
}
</script>

<style lang="scss" scoped>
.row {
  margin: 0;
  padding: 0;
}

a {
  text-decoration: none;
}

.header {
  position: absolute;
  width: 100%;

  &__title {
    color: white;
    font-size: $title-size-mobile;
    font-family: $title-fontFamily;
    text-align: center;
    text-shadow: $text-shadow;
    width: fit-content;
    z-index: 1;
  }
}

.imageBox {
  align-items: center;
  display: flex;
  // height: 360px;
  justify-content: center;
  position: relative;

  img {
    // height: 360px;
    filter: brightness(70%);
    object-fit: fill;
  }

  &__link {
    border: 3px solid rgb(255, 255, 255);
    color: white;
    letter-spacing: 0.2em;
    position: absolute;
    padding: $pad-imageBoxes;
    text-align: center;
    z-index: 1;
  }

  &__text {
    font-size: $subtitle-size-mobile;
    font-family: $subtitle-fontFamily;
    font-weight: bold;
    text-shadow: $text-shadow;
  }
}

@media (min-width: 768px) {
  section {
    height: 100vh;
  }
  .imageBox {
    &__link {
      transform: rotate(270deg);
    }
  }
}
@media (min-width: 1200px) {
  .imageBox {
    &__link {
      transform: rotate(0deg);
    }
  }
}

/** Animation when the page loads - Place all elements on the viewport */
//Galerie
@keyframes galerie {
  from {
    transform: translateX(-100%);
  }
}
.row .Galerie {
  animation: galerie $time-animation;
}

// musiques
@keyframes musiques {
  from {
    transform: translateX(100%);
  }
}
.row .Musiques {
  animation: musiques $time-animation;
}

//presentation
@keyframes presentation {
  from {
    transform: translateX(-100%);
  }
}
.row .Presentation {
  animation: presentation $time-animation;
}

//Projets
@keyframes projets {
  from {
    transform: translateX(100%);
  }
}
.row .Projets {
  animation: projets $time-animation;
}

//Instruments
@keyframes instruments {
  from {
    transform: translateX(-100%);
  }
}
.row .Instruments {
  animation: instruments $time-animation;
}

@media (min-width: 768px) {
  .imageBox {
    height: 100%;

    picture,
    img {
      object-fit: cover;
      height: 100%;
    }
  }
  /** Animation when the page loads - Place all elements on the viewport */
  //Galerie
  @keyframes galerie {
    from {
      transform: translateY(-100%);
    }
  }
  .row .Galerie {
    animation: galerie $time-animation;
  }

  // musiques
  @keyframes musiques {
    from {
      transform: translateY(100%);
    }
  }
  .row .Musiques {
    animation: musiques $time-animation;
  }

  //presentation
  @keyframes presentation {
    from {
      transform: translateY(-100%);
    }
  }
  .row .Presentation {
    animation: presentation $time-animation;
  }

  //Projets
  @keyframes projets {
    from {
      transform: translateY(100%);
    }
  }
  .row .Projets {
    animation: projets $time-animation;
  }

  //Instruments
  @keyframes instruments {
    from {
      transform: translateY(-100%);
    }
  }
  .row .Instruments {
    animation: instruments $time-animation;
  }
}
</style>
