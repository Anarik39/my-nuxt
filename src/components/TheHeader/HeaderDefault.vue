<template>
  <v-app-bar :elevation="4">
    <v-container>
      <nav class="d-flex align-center">
        <v-toolbar-title>
          <v-btn
            variant="text"
            to="/"
          >
            <nuxt-img
              preload
              src="/img/logo.webp"
              width="30px"
              class="mr-2"
              alt="logo"
            />

            <span>AAnar1k</span>
          </v-btn>
        </v-toolbar-title>

        <v-spacer />

        <template v-if="isLoading && !mobile">
          <header-nav />

          <v-divider
            class="mx-2"
            inset
            vertical
          />
        </template>

        <ui-button-toggle-theme />

        <template v-if="isLoading && mobile">
          <v-divider
            class="mx-2"
            inset
            vertical
          />

          <v-app-bar-nav-icon
            aria-label="open menu"
            @click="emit('open-drawer')"
          >
            <v-icon size="x-large">
              mdi-menu
            </v-icon>
          </v-app-bar-nav-icon>
        </template>
      </nav>
    </v-container>
  </v-app-bar>
</template>

<script setup lang="ts">
import { useDisplay } from 'vuetify';
import HeaderNav from '~/components/TheHeader/HeaderNav.vue';
import UiButtonToggleTheme from '~/components/Ui/UiButtonToggleTheme.vue';

const emit = defineEmits<{(e: 'open-drawer'): void}>();

const { mobile } = useDisplay();
const isLoading = ref<boolean>(false);

onMounted(() => {
  isLoading.value = true;
});
</script>
