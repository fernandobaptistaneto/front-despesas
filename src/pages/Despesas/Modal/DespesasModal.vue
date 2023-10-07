<template>
  <Modal>
    <template #body>
      teste fernando amorim
    </template>
  </Modal>
</template>
<script>
import Events from 'src/core/event-bus.js';
import { onMounted, ref, watch, defineAsyncComponent } from 'vue';

export default {
  name: 'DespesasModal',
  props: {
  },
  components: {
    Modal: defineAsyncComponent(() => import('src/components/modal/modal.vue'))
  },
  setup(props) {

    const showModal = ref(false)

    // watch(showModal, () => {

    // })

    onMounted(() => {
      Events.on('open::modal::despesas', (v) => {
        showModal.value = v
        Events.emit('open::modal::default', showModal.value)
      })
    })

    return {
      showModal,
      props
    }
  }
}
</script>
<style lang="scss" scoped></style>