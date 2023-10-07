<template>
  <div class="container-menu">
    <div style="max-width: 350px" v-if="grupo">
      <!-- Criação do item de grupo -->
      <q-expansion-item :duration="200" icon="mail" :label="grupo">
        <div v-if="subGrupo">
          <!-- Criação do item de subgrupo -->
          <q-expansion-item :duration="200" class="label-menu" :header-inset-level="1" expand-separator icon="receipt"
            :label="subGrupo">
            <!-- Criação do item de menu dentro do subgrupo -->
            <q-expansion-item dense-toggle :label="label" :header-inset-level="1" :content-inset-level="2"
              class="label-menu" expand-icon="none" :to="routerLink"></q-expansion-item>
          </q-expansion-item>
        </div>
        <div v-if="!subGrupo">
          <!-- Criação do item de menu dentro do grupo -->
          <q-expansion-item class="item-menu" :duration="200" :label="label" expand-icon="none"
            :to="routerLink"></q-expansion-item>
        </div>
      </q-expansion-item>
    </div>
    <div v-if="!grupo && !subGrupo && label" style="max-width: 350px">
      <!-- Criação do item de menu fora de grupo e subgrupo -->
      <q-expansion-item :duration="200" icon="mail" :label="label" expand-icon="none" :to="routerLink"></q-expansion-item>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'EssentialLink',
  props: {
    grupo: {
      type: String,
      default: null
    },
    subGrupo: {
      type: String,
      default: null
    },
    label: {
      type: String,
      required: true
    },

    icon: {
      type: String,
      default: ''
    },

    routerLink: {
      type: String,
      default: ''
    }
  },
  // eslint-disable-next-line space-before-function-paren
  data() {
    return {
      showSubMenu: false
    }
  },
  methods: {
    // eslint-disable-next-line space-before-function-paren
    toggleSubMenu() {
      this.showSubMenu = !this.showSubMenu
    }
  }
})
</script>
<style scooped lang="scss">
.menu {
  color: white;
  background-color: #283747;
  text-decoration: none;
  padding: 0px;
}

.container-menu {
  .label-menu {
    .q-item {
      padding-left: 30px !important;
    }
  }

  .item-menu {
    .q-icon .notranslate .material-icons {
      font-size: 5px;
    }
  }
}
</style>
