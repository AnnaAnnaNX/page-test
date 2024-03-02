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
    <div style="display: flex; justify-content: center; align-items: center; flex-direction: column;">
      <div
        :style="{background: image ? `url(${image})` : '#c4c4c4'}"
        class="avatar"
      >
        <div v-if="!image">{{avatarText}}</div>
      </div>
      <p>Перетащите или выберети фото на компьютере</p>
      <v-file-input
        clearable
        v-model="chosenFile"
        @change="onFileChange"
        base-color="white"
        bg-color="white"
        color="white"
        @click:clear="clear"
        class="file-input"
      >
        <template v-slot:label></template>
        <template v-slot:selection></template>
        <template v-slot:prepend-inner>
          <div v-if="!image" class="title">Выберите файл</div>
          <div v-if="image" class="title">{{fileName}}</div>
        </template>
      </v-file-input>
    </div>

    <div>
      <v-row>
        <v-col cols="6">
          <label>Фамилия</label>
          <v-text-field v-model="form.name"></v-text-field>
        </v-col>
        <v-col cols="6">
          <label>Имя</label>
          <v-text-field v-model="form.firstName"></v-text-field>
        </v-col>
      </v-row>
    </div>
{{form}}
  </div>
</template>

<script setup>
import {computed, ref} from 'vue'

const chosenFile = ref(null)
const image = ref(null)
const fileName = ref('')
const form = ref({})
const avatarText = computed(() => {
  return `${form.value?.name?.[0] || ''}${form.value?.firstName?.[0] || ''}`
})

const onFileChange = function(file) {
    const reader = new FileReader()
    reader.readAsDataURL(chosenFile.value[0])
    fileName.value = chosenFile.value[0].name
    reader.onload = () => {
      image.value = reader.result
    }
}
const clear = () => {
  image.value = null
  fileName.value = ''
}
</script>

<style>
.button-text {
  text-transform: capitalize;
}
.file-input {
  background-color: white!important;
}
.title {
  min-width: 300px;
  color: orange;
}
.avatar {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  color: grey;
  font-size: 70px;
  text-transform: uppercase;
}
</style>
