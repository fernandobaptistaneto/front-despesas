<template>
  <div class="pagina">
    <div class="row justify-start">
      <q-card-section class="text-black title">
        <div class="text-h6">Minhas Despesas</div>
      </q-card-section>
      <!-- <span class="text-weight-bold text-blue-8"> {{ usuarioLogado }}</span> -->
    </div>
    <div class="q-pa row q-gutter-md q-mx-xl cards">
      <q-card
        v-ripple
        @click="editItem(item)"
        class="card-fixed-size cursor-pointer q-hoverable"
        v-for="item in despesas"
        :key="item"
        bordered
      >
        <span class="q-focus-helper"></span>
        <div>
          <div class="img-despesa">
            <q-img src="/src/assets/despesa.png" />
          </div>
        </div>
        <q-separator />
        <div class="label-card">
          <q-card-section class="q-pt-none">
            <div class="text-h6">
              <span>{{ item.name }}</span>
            </div>
          </q-card-section>
        </div>
        <q-card-section>
          <span><a class="text-h6">Descrição: </a></span>
          <q-space></q-space>
          <div class="row description">
            <div class="description-content">{{ item.description }}</div>
          </div>
        </q-card-section>
      </q-card>
    </div>
  </div>

  <DespesasModal />
</template>
  
  <script>
import { defineAsyncComponent, defineComponent, ref, computed } from "vue";

import Events from "src/core/event-bus.js";

import { sharedData } from "../store.js";

export default defineComponent({
  name: "Despesas",
  components: {
    // Modal: defineAsyncComponent(() => import('src/components/modal/modal.vue'))
    // DespesasModal: defineAsyncComponent(() =>
    //   import("./components/DespesasModal.vue")
    // ),
  },
  setup() {
    const usuarioLogado = ref("Fernando Baptista");

    const despesas = [
      {
        id: 1,
        name: "Minhas Despesas",
        description:
          "SLKPALPSDAKÇALSKDjlkjsahdlkjs hdaskl djklasj daksljd klasj lkjqiowuewioqu askjdklsa SLKPALPSDAKÇALSKDjlkjsahdlkjs hdaskl djklasj daksljd klasj lkjqiowuewioqu askjdklsa SLKPALPSDAKÇALSKDjlkjsahdlkjs hdaskl djklasj daksljd klasj lkjqiowuewioqu askjdklsa",
      },
      {
        id: 2,
        name: "Despesas Débita",
        description: "Fsajdikasjlk",
      },
      {
        id: 3,
        name: "Despesas Joãoo",
        description: "SLKPALPSDAKÇALSKDjlkjsahdlkjs hdaskl djklasj daksl",
      },
      {
        id: 4,
        name: "Minhas Despesas",
        description: "1",
      },
      {
        id: 5,
        name: "Minhas Despesas",
        description: "2",
      },
      {
        id: 6,
        name: "Minhas Despesas",
        description: "13",
      },
      {
        id: 10,
        name: "Despesas Fernando Amorim",
        description: "45",
      },
    ];

    const editItem = (item) => {
      Events.emit("mudar::tela::despesas", "DespesasView");
      sharedData.value = item;
    };

    return {
      usuarioLogado,
      despesas,
      editItem,
    };
  },
});
</script>
  
  <style scoped lang="scss">

  
.title {
  text-transform: uppercase;
  font-weight: bold;
}
.cards {
  display: flex;
  justify-content: space-between;
}

.img-despesa {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  /* Definir altura para ocupar a altura total do card */
  max-width: 150px;
  margin: 0 auto;
  /* Centralizar horizontalmente a imagem */
  padding: 30px;
}

/* Para garantir que a imagem não estique, defina max-height também */
.img-despesa img {
  max-height: 100%;
  width: auto;
  /* Para manter a proporção da imagem */
}

.q-card {
  border-radius: 10px;

  .q-card--bordered {
    border: 2px solid rgba(0, 0, 0, 0.12);
  }
}

.label-card {
  display: grid;
  justify-content: center;
  align-items: center;
  margin: 0 auto;
}

.q-card__section--vert {
  padding: 10px;
  font-size: 12px;
}

.card-fixed-size {
  min-width: 45%;
  max-width: 45%;
  margin-top: 50px;

  @media (max-width: 462px) {
    min-width: 95%;
    justify-content: center;
  }
}

.description {
  /* Use flexbox para controlar o fluxo do conteúdo */
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  /* Alinhe o conteúdo ao topo */
  align-items: flex-start;
  /* Alinhe o conteúdo à esquerda */
  max-height: 150px;
  /* Ajuste conforme necessário */
  overflow-y: auto;
  /* Adicione uma barra de rolagem vertical se o conteúdo exceder a altura máxima */
}
</style>