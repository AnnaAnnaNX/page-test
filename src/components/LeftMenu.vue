<template>
  <v-list density="compact" bg-color="secondary" style="background: #212121;">
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
    name: 'Обо мне',
    id: 1,
  },
  {
    name: 'Документы',
    id: 2,
  },
  {
    name: 'Объекты',
    id: 3,
  },
  {
    name: 'Календарь работ',
    id: 4,
  },
  {
    name: 'Отклики',
    id: 5,
  }
]
</script>
