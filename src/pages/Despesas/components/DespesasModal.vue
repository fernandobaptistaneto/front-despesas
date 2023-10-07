<template>
  <Modal :title="despesa.name">
    <template #body> teste fernando amorim </template>
  </Modal>
</template>
<script>
// import { cloneDeep } from 'lodash';

import Events from "src/core/event-bus.js";
import { onMounted, ref, defineAsyncComponent, reactive } from "vue";

export default {
  name: "DespesasModal",
  props: {},
  components: {
    Modal: defineAsyncComponent(() => import("src/components/modal/modal.vue")),
  },
  setup(props) {
    const showModal = ref(false);
    const despesa = reactive({});

    // watch(showModal, () => {

    // })

    onMounted(() => {
      Events.on("open::modal::despesas", (item) => {
        Object.assign(despesa, item);
        showModal.value = true;
        Events.emit("open::modal::default", showModal.value);
      });
    });

    return {
      showModal,
      props,
      despesa,
    };
  },
};
</script>
<style lang="scss" scoped></style>