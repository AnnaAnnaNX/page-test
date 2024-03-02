<template>
  <div style="padding: 20px;">
    <div>
      <v-btn prepend-icon="mdi-chevron-left" variant="text">
        <span class="button-text">Объекты</span>
      </v-btn>
      <span style="font-weight: 600; font-size: 25px;">Редактировать профиль</span>
    </div>
    <p style="font-weight: 600; font-size: 12px; padding: 20px; padding-top: 30px;">
      Основная информация
    </p>
    <v-divider></v-divider>
    <div>
      <v-img v-if="image" :src="image" />
      <p>Перетащите или выберети фото на компьютере</p>
      <v-file-input
        :label="chosenFile ? '' : 'Выбрать файл'"
        v-model="chosenFile"
        @change="onFileChange"
      ></v-file-input>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const chosenFile = ref(null)
const image = ref(null)

const onFileChange = function(file) {
    const reader = new FileReader()
    reader.readAsDataURL(chosenFile.value[0])
    reader.onload = () => {
        image.value = reader.result
    }
}
</script>

<style scoped>
.button-text {
  text-transform: capitalize;
}
</style>
