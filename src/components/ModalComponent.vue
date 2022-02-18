<template>
  <ion-modal
    ref="modal"
    :is-open="isOpen"
    :breakpoints="[0, 0.5, 1]"
    :initialBreakpoint="1"
    @ionModalDidDismiss="onDidDismiss"
  >
    <ion-button @click="closeModal">Close modal</ion-button>
    <ion-button @click="closeModalAndRemoveShowModalClass"
      >Close modal and remove show-modal class</ion-button
    >
  </ion-modal>
</template>
<script lang="ts">
import { IonModal, modalController, IonButton } from "@ionic/vue";
import { defineComponent, ref } from "vue";
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
    const modal = ref();
    const doBug = ref(false);
    const closeModal = () => {
      doBug.value = true;
      modalController.dismiss();
    };

    const closeModalAndRemoveShowModalClass = () => {
      doBug.value = false;
      modalController.dismiss();
    };

    const onDidDismiss = () => {
      if (!doBug.value) {
        modal.value.$el.classList.remove("show-modal");
      }
      emit("update:isOpen", false);
    };
    return {
      modal,
      closeModal,
      closeModalAndRemoveShowModalClass,
      onDidDismiss,
    };
  },
});
</script>

<style scoped></style>
