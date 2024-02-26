<template>
  <q-layout class="layout" view="lHh Lpr lFf">
    <q-header>
      <q-toolbar style="align-items: center">
        <div class="small-screen-only q-mx-auto full-width">
          <div class="flex justify-between">
           <q-btn to="/" flat no-caps>
              <div class="text-h5 text-weight-medium text-center" style="color: #262626">
              Beats/Minute App
              
              </div>
            </q-btn>
            <q-btn
              flat
              no-caps
              dense
              icon="menu"
              style="color: #262626"
              aria-label="Menu"
              @click="toggleLeftDrawer"
              class="small-screen-only q-my-auto"
            />
          </div>
        </div>

        <div
          class="large-screen-only"
          style="display: flex; align-items: center"
        >
     <q-btn
            class="large-screen-only q-px-xl q-mr-lg"
            no-caps
            href="https://github.com/Noxxider"
            text-color="dark"
            target="_blank"
            label="GitHub"
            style="padding: 8px 12px"
            unelevated
          />
 
          <q-btn
            class="large-screen-only q-px-xl q-mr-lg"
            no-caps
            href="https://ravinojuwono.com/weighttracker"
            text-color="dark"
            target="_blank"
            label="Weight Tracker"
            style="padding: 8px 12px"
            unelevated
          />

          <q-btn
            class="large-screen-only q-px-xl "
            no-caps
            href="https://ravinojuwono.com/contact"
            target="_blank"
            text-color="dark"
            label="Contact"
            style="padding: 8px 12px"
            unelevated
          />

        </div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" :width="200" bordered behavior="mobile">
      <q-list>
        <div class="text-h6 q-pa-md" header>Pages</div>
        <q-separator />
        <EssentialLink
          class="q-mt-sm"
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";
import EssentialLink from "components/EssentialLink.vue";

const linksList = [
  {
    title: "Home",
    icon: "home",
    link: "/",
  },
  {
    title: "GitHub",
    icon: "code",
    link: "https://github.com/Noxxider/",
  },

  {
    title: "Contact",
    icon: "phone",
    link: "https://ravinojuwono.com/contact",
  },
];

export default defineComponent({
  name: "MainLayout",

  components: {
    EssentialLink,
  },

  setup() {
    const leftDrawerOpen = ref(false);

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});
</script>
