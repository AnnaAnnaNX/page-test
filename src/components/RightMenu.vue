<template>
  <v-list density="compact" bg-color="white" style="background: #212121; padding-left: 30px; padding-right: 30px;">
    <v-list-item
      v-for="(item, i) in items"
      :key="i"
      :value="item"
      :href="'/'"
      color="primary"
    >
      <v-list-item-title v-text="item.name"></v-list-item-title>
    </v-list-item>
  </v-list>
</template>

<script setup>
  const items = [
    {
      name: 'Основная информация',
      id: 1,
    },
    {
      name: 'Квалификационные документы',
      id: 2,
    },
    {
      name: 'Образование',
      id: 3,
    },
    {
      name: 'Контакты',
      id: 4,
    },
    {
      name: 'Данные для рассчетов',
      id: 5,
    },
    {
      name: 'Виды работ',
      id: 6,
    },
    {
      name: 'Дополнительные данные',
      id: 7,
    }
  ]
</script>
