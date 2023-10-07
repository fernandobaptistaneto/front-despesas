<template>
  <div class="q-pa-md q-gutter-sm">
    <q-dialog v-model="showModal" persistent transition-show="scale" transition-hide="scale">
      <q-card class="bg-white text-white modal">
        <q-card-section class="row items-center q-pt-lg header">
          <div class="text-h6">{{ title }}</div>
          <q-space />
          <q-btn icon="close" @click="showModal = false" flat round dense v-close-popup color="black" />
        </q-card-section>

        <q-separator />

        <q-card-section class="scroll body">
          <slot name="body">
          </slot>
        </q-card-section>

        <q-card-actions align="right">

        </q-card-actions>
      </q-card>
    </q-dialog>
  </div>
</template>
<script>
import Events from 'src/core/event-bus.js';
import { onMounted, ref } from 'vue';

export default {
  name: 'modal',
  props: {
    title: {
      type: String,
      default: 'Titulo do Modal'
    }
  },
  setup(props) {

    const showModal = ref(false)


    onMounted(() => {
      Events.on('open::modal::default', (v) => {
        showModal.value = v
        console.log('default');
      })
    })

    return {
      showModal,
      props
    }
  }
}
</script>

<style lang="scss" scoped>
.modal {
  width: 500px;
  height: 500px;
}

.header {
  color: #000000;
}

.body {
  color: #000000;
}
</style>