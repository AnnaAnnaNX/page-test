<template>
  <v-toolbar density="compact" style="background: white; border-bottom: 1px solid #bbb7b7;">
    <v-btn prepend-icon="mdi-card-account-details-outline" variant="text">
      <span class="button-text">Вакансии</span>
    </v-btn>
    <v-btn prepend-icon="mdi-domain" variant="text">
      <span class="button-text">Объекты</span>
    </v-btn>
    <v-spacer></v-spacer>
    <v-btn prepend-icon="mdi-heart-outline" variant="text">
      <span class="button-text">Избранное</span>
    </v-btn>
    <v-btn prepend-icon="mdi-bell-outline" variant="text">
      <span class="button-text">Уведомления</span>
    </v-btn>
    <span style="margin-right: 50px; font-size: 14px; font-weight: 500;">
      <v-avatar color="white" size="x-small">
        АБ
      </v-avatar>
      Профиль
    </span>
  </v-toolbar>
</template>

<script setup>
import { mdiCardAccountDetailsOutline } from '@mdi/js';
import {ref} from 'vue'
const path = ref(mdiCardAccountDetailsOutline)
</script>

<style scoped>
  .button-text {
    text-transform: capitalize;
  }
</style>
