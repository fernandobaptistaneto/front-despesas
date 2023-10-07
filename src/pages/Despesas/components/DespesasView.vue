<template>
  <div class="pagina">
    <div class="text-h6 row justify-center">
      Despesa: &nbsp;
      <span class="text-weight-bold text-blue-8">
        {{ dadosCompartilhados.name }}</span
      >
    </div>
    <q-btn @click="backPage"> Voltar </q-btn>
  </div>
</template>
  
  <script>
import { defineAsyncComponent, defineComponent, ref, computed } from "vue";

import Events from "src/core/event-bus.js";
import { sharedData } from "../store.js";

export default defineComponent({
  name: "DespesasDetalhe",
  components: {
    // Modal: defineAsyncComponent(() => import('src/components/modal/modal.vue'))
  },
  setup() {
    const dadosCompartilhados = computed(() => sharedData.value);

    const backPage = () => {
      Events.emit("mudar::tela::despesas", "DespesasList");
    };

    return {
      backPage,
      dadosCompartilhados,
    };
  },
});
</script>
  
  <style scoped lang="scss">
.pagina {
  padding-top: 30px;
}
</style>