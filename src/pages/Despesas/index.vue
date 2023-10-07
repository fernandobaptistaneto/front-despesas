<template>
  <div class="pagina">
    <!-- Se telaAtiva for 'ListaDespesas', mostre o componente ListaDespesas -->
    <component :is="telaAtiva" />
  </div>
</template>

<script>
import { defineAsyncComponent, defineComponent, ref, computed } from "vue";
import Events from "src/core/event-bus.js";

export default {
  name: "Despesas",
  components: {
    // Modal: defineAsyncComponent(() => import('src/components/modal/modal.vue'))
    DespesasList: defineAsyncComponent(() =>
      import("./components/DespesasList.vue")
    ),
    DespesasView: defineAsyncComponent(() =>
      import("./components/DespesasView.vue")
    ),
  },
  setup() {
    const telaAtiva = ref("DespesasList");

    Events.on("mudar::tela::despesas", (v) => {
      telaAtiva.value = v;
    });

    const mudarTela = () => {
      telaAtiva.value =
        telaAtiva.value === "DespesasView" ? "DespesasList" : "DespesasView";
    };

    return {
      telaAtiva,
      mudarTela,
    };
  },
};
</script>

<style scoped lang="scss">
.pagina {
  padding-top: 30px;
}
</style>