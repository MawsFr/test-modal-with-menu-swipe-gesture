<template>
  <ion-modal
    :is-open="isOpen"
    :breakpoints="[0, 0.5, 1]"
    :initialBreakpoint="1"
    @ionModalDidDismiss="onDidDismiss"
  >
    <ion-button @click="closeModal">Close modal</ion-button>
  </ion-modal>
</template>
<script lang="ts">
import { IonModal, modalController, IonButton } from "@ionic/vue";
import { defineComponent } from "vue";
export default defineComponent({
  components: {
    IonModal,
    IonButton,
  },
  props: {
    isOpen: {
      type: Boolean,
      default: false,
    },
  },
  setup(_props, { emit }) {
    const closeModal = () => {
      modalController.dismiss();
    };
    const onDidDismiss = () => {
      emit("update:isOpen", false);
    };
    return { closeModal, onDidDismiss };
  },
});
</script>

<style scoped></style>
