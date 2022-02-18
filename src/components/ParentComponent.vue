<template>
  <ion-button @click="openModal"> Open Modal </ion-button>
  <ModalComponent v-model:isOpen="isOpen"></ModalComponent>
</template>
<script lang="ts">
import { defineComponent, ref } from "vue";
import ModalComponent from "./ModalComponent.vue";
import { IonButton } from "@ionic/vue";

export default defineComponent({
  components: {
    ModalComponent,
    IonButton,
  },
  setup() {
    const isOpen = ref(false);
    const openModal = () => {
      isOpen.value = true;
    };
    return {
      isOpen,
      openModal,
    };
  },
});
</script>

<style scoped></style>
