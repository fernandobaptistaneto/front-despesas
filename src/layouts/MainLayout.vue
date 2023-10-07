<template>
  <div>
    <q-layout view="lHh Lpr lFf">
      <q-header elevated>
        <q-toolbar>
          <q-btn
            flat
            dense
            round
            @click="toggleLeftDrawer"
            icon="menu"
            aria-label="Menu"
          />
          <q-toolbar-title> Gestão de Despesas </q-toolbar-title>
          <q-space />
          <div class="q-gutter-sm row items-center no-wrap">
            <!-- <q-btn round dense flat color="white" :icon="$q.fullscreen.isActive ? 'fullscreen_exit' : 'fullscreen'"
                           @click="$q.fullscreen.toggle()"
                           v-if="$q.screen.gt.sm">
                    </q-btn> -->
            <!-- <q-btn round dense flat color="white" icon="notifications">
            <q-badge color="red" text-color="white" floating>
              5
            </q-badge>
            <q-menu
            >
              <q-list style="min-width: 100px">
                <messages></messages>
                <q-card class="text-center no-shadow no-border">
                  <q-btn label="View All" style="max-width: 120px !important;" flat dense
                         class="text-indigo-8"></q-btn>
                </q-card>
              </q-list>
            </q-menu>
          </q-btn> -->
            <q-btn round flat>
              <q-avatar size="26px">
                <img src="https://cdn.quasar.dev/img/boy-avatar.png" />
              </q-avatar>
            </q-btn>
          </div>
        </q-toolbar>
      </q-header>

      <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        bordered
        class="bg-primary text-white"
      >
        <q-list>
          <q-item to="/" active-class="q-item-no-link-highlighting">
            <q-item-section avatar>
              <q-icon name="dashboard" />
            </q-item-section>
            <q-item-section>
              <q-item-label>Dashboard</q-item-label>
            </q-item-section>
          </q-item>

          <q-item to="/Dashboard2" active-class="q-item-no-link-highlighting">
            <q-item-section avatar>
              <q-icon name="dashboard" />
            </q-item-section>
            <q-item-section>
              <q-item-label>CRM Dashboard</q-item-label>
            </q-item-section>
          </q-item>

          <q-expansion-item icon="pages" label="Pages">
            <q-list class="q-pl-lg">
              <q-item to="/Login-1" active-class="q-item-no-link-highlighting">
                <q-item-section avatar>
                  <q-icon name="email" />
                </q-item-section>
                <q-item-section>
                  <q-item-label>Login-1</q-item-label>
                </q-item-section>
              </q-item>

              <q-item to="/Lock" active-class="q-item-no-link-highlighting">
                <q-item-section avatar>
                  <q-icon name="lock" />
                </q-item-section>
                <q-item-section>
                  <q-item-label>Lock Screen</q-item-label>
                </q-item-section>
              </q-item>

              <q-item to="/Lock-2" active-class="q-item-no-link-highlighting">
                <q-item-section avatar>
                  <q-icon name="lock" />
                </q-item-section>
                <q-item-section>
                  <q-item-label>Lock Screen - 2</q-item-label>
                </q-item-section>
              </q-item>
              <q-item to="/Pricing" active-class="q-item-no-link-highlighting">
                <q-item-section avatar>
                  <q-icon name="list" />
                </q-item-section>
                <q-item-section>
                  <q-item-label>Pricing</q-item-label>
                </q-item-section>
              </q-item>

              <q-item-label header class="text-weight-bolder text-white"
                >Generic</q-item-label
              >
              <q-item to="/Profile" active-class="q-item-no-link-highlighting">
                <q-item-section avatar>
                  <q-icon name="person" />
                </q-item-section>
                <q-item-section>
                  <q-item-label>User Profile</q-item-label>
                </q-item-section>
              </q-item>

              <q-item
                to="/Maintenance"
                active-class="q-item-no-link-highlighting"
              >
                <q-item-section avatar>
                  <q-icon name="settings" />
                </q-item-section>
                <q-item-section>
                  <q-item-label>Maintenance</q-item-label>
                </q-item-section>
              </q-item>
            </q-list>
          </q-expansion-item>

          <q-expansion-item icon="map" label="Maps">
            <q-list class="q-pl-lg">
              <q-item to="/Map" active-class="q-item-no-link-highlighting">
                <q-item-section avatar>
                  <q-icon name="map" />
                </q-item-section>
                <q-item-section>
                  <q-item-label>Map</q-item-label>
                </q-item-section>
              </q-item>

              <q-item
                to="/MapMarker"
                active-class="q-item-no-link-highlighting"
              >
                <q-item-section avatar>
                  <q-icon name="location_on" />
                </q-item-section>
                <q-item-section>
                  <q-item-label>Map Marker</q-item-label>
                </q-item-section>
              </q-item>

              <q-item
                to="/StreetView"
                active-class="q-item-no-link-highlighting"
              >
                <q-item-section avatar>
                  <q-icon name="streetview" />
                </q-item-section>
                <q-item-section>
                  <q-item-label>Street View</q-item-label>
                </q-item-section>
              </q-item>
            </q-list>
          </q-expansion-item>

          <q-item to="/Despesas" active-class="q-item-no-link-highlighting">
            <q-item-section avatar>
              <q-icon name="table_chart" />
            </q-item-section>
            <q-item-section>
              <q-item-label>Despesas</q-item-label>
            </q-item-section>
          </q-item>

          <!--        not completed-->
          <!--        <q-item to="/Taskboard" active-class="q-item-no-link-highlighting">-->
          <!--          <q-item-section avatar>-->
          <!--            <q-icon name="done"/>-->
          <!--          </q-item-section>-->
          <!--          <q-item-section>-->
          <!--            <q-item-label>Taskboard</q-item-label>-->
          <!--          </q-item-section>-->
          <!--        </q-item>-->

          <!-- <q-item to="/Pagination" active-class="q-item-no-link-highlighting">
          <q-item-section avatar>
            <q-icon name="date_range"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>Pagination</q-item-label>
          </q-item-section>
        </q-item>
        <q-item to="/Ecommerce" active-class="q-item-no-link-highlighting">
          <q-item-section avatar>
            <q-icon name="shopping_cart"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>Product Catalogues</q-item-label>
          </q-item-section>
        </q-item>
        <q-expansion-item
          icon="menu_open"
          label="Menu Levels"
        >
          <q-item class="q-ml-xl" active-class="q-item-no-link-highlighting">
            <q-item-section>
              <q-item-label>Level 1</q-item-label>
            </q-item-section>
          </q-item>
          <q-expansion-item
            :header-inset-level="0.85"
            label="Level 2"
          >
            <q-item class="q-ml-xl" style="margin-left: 55px  !important;" active-class="q-item-no-link-highlighting">
              <q-item-section>
                <q-item-label>Level 2.1</q-item-label>
              </q-item-section>
            </q-item>
            <q-expansion-item
              :header-inset-level="1"
              label="Level 2.2"
            >
              <q-item style="margin-left: 65px  !important;" active-class="q-item-no-link-highlighting">
                <q-item-section>
                  <q-item-label>Level 2.2.1</q-item-label>
                </q-item-section>
              </q-item>
              <q-item style="margin-left: 65px  !important;" active-class="q-item-no-link-highlighting">
                <q-item-section>
                  <q-item-label>Level 2.2.2</q-item-label>
                </q-item-section>
              </q-item> -->
          <!-- </q-expansion-item>
          </q-expansion-item>
        </q-expansion-item> -->
        </q-list>
      </q-drawer>

      <q-page-container class="bg-grey-2">
        <q-page class="q-pa-sm">
          <q-breadcrumbs gutter="sm">
            <q-breadcrumbs-el label="Home" />
            <q-breadcrumbs-el label="Components" />
            <q-breadcrumbs-el label="Breadcrumbs" />
          </q-breadcrumbs>
          <q-spacer />
          <!-- <q-responsive :ratio="1" class="col"> -->
          <q-card class="card-container">
            <transition name="slide-fade" mode="out-in">
              <router-view />
            </transition>
          </q-card>
          <!-- </q-responsive> -->
        </q-page>
      </q-page-container>

      <q-footer elevated class="bg-grey-8 text-white">
        <q-toolbar class="footer">
          <q-toolbar-title>
            <span>© 2023 | Todos os direitos reservados.</span>
          </q-toolbar-title>
        </q-toolbar>
      </q-footer>
    </q-layout>
  </div>
</template>

<script>
import EssentialLink from "components/EssentialLink.vue";
import { useQuasar } from "quasar";
import { defineComponent, ref } from "vue";
import Messages from "./Messages.vue";

export default defineComponent({
  name: "MainLayout",

  components: {
    EssentialLink,
    Messages,
  },

  setup() {
    const leftDrawerOpen = ref(false);
    const $q = useQuasar();

    return {
      $q,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});
</script>

<style scoped lang="scss">
* {
  margin: 0;
}

.q-breadcrumbs {
  margin-bottom: 5px;
  margin-left: 0;
}

.fa-beat {
  animation: fa-beat 5s ease infinite;
}

@keyframes fa-beat {
  0% {
    transform: scale(1);
  }

  5% {
    transform: scale(1.25);
  }

  20% {
    transform: scale(1);
  }

  30% {
    transform: scale(1);
  }

  35% {
    transform: scale(1.25);
  }

  50% {
    transform: scale(1);
  }

  55% {
    transform: scale(1.25);
  }

  70% {
    transform: scale(1);
  }
}

.footer {
  min-height: 35px;

  .q-toolbar__title {
    font-size: 14px;
  }
}

.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.2s cubic-bezier(1, 0.2, 0.2, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  opacity: 0;
}

.card-container {
  min-height: 89vh;
  // padding-bottom: 40px;
  // padding-top: 15px;
  padding: 8px 12px 12px 12px;
}
</style>
