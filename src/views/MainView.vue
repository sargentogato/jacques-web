<template>
  <div class="container-fluid">
    <HeaderMain :title="title" :imageText="imageText" />
    <SectionMain :imageText="imageText" @addModal="openModal($event)" />
    <Teleport to="#modal">
      <Modal :show="showModal" @close="showModal = false">
        <template #content>
          <Catering v-if="infoToShow === 'Catering'" />
          <Cooking v-if="infoToShow === 'Cooking'" />
          <Corsi v-if="infoToShow === 'Corsi di'" />
        </template>
      </Modal>
    </Teleport>
  </div>
</template>

<script setup>
import HeaderMain from "../components/MainHeader.vue";
import SectionMain from "../components/MainSection.vue";
import Modal from "../components/Modal.vue";
import Catering from "../components/Catering.vue";
import Cooking from "../components/Cooking.vue";
import Corsi from "../components/Corsi.vue";
import { imageText } from "../info/info.js";

import { ref } from "vue";

let showModal = ref(false);
let infoToShow = ref();
let title = ref("Jacques Madjar");

function openModal(event) {
  infoToShow = event;
  showModal.value = true;
}
</script>

<style lang="scss" scoped>
.container-fluid {
  padding: 0;
}

@media (width >767px) {
  .container-fluid {
    overflow: hidden;
  }
}
</style>
