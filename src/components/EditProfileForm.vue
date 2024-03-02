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
        accept="image/png, image/jpeg, image/bmp"
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
        <v-col cols="6" class="col">
          <label>Фамилия</label>
          <v-text-field v-model="form.name" variant="outlined"></v-text-field>
        </v-col>
        <v-col cols="6" class="col">
          <label>Имя</label>
          <v-text-field v-model="form.firstName" variant="outlined"></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col class="col">
          <label>Статус</label>
          <v-select
              clearable
              :items="['California', 'Colorado', 'Florida', 'Georgia', 'Texas', 'Wyoming']"
              variant="outlined"
              v-model="form.status"
          ></v-select>
        </v-col>
      </v-row>
      <v-row>
        <v-col class="col">
          <label>Гражданство</label>
          <v-select
              clearable
              :items="['California', 'Colorado', 'Florida', 'Georgia', 'Texas', 'Wyoming']"
              variant="outlined"
              v-model="form.country"
          ></v-select>
        </v-col>
      </v-row>
      <v-row>
        <v-col class="col">
          <label>Готовность переехать</label>
          <v-select
              clearable
              :items="['California', 'Colorado', 'Florida', 'Georgia', 'Texas', 'Wyoming']"
              variant="outlined"
              v-model="form.readyRelocate"
          ></v-select>
        </v-col>
      </v-row>
      <v-row>
        <v-col class="col">
          <label>Дата рождения</label>
          <v-text-field @click="showCalender = !showCalender" :value="form?.date?.toISOString()?.split('T')?.[0]" variant="outlined"></v-text-field>
          <v-date-picker v-if="showCalender" v-model="form.date" @update:modelValue="showCalender = false"></v-date-picker>
        </v-col>
      </v-row>
      <v-row>
        <v-col class="col">
          <label>Основная специальность</label>
          <v-text-field v-model="form.readyRelocate" variant="outlined"></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col class="col">
          <v-switch label="Стропальщик" v-model="form.slinger" color="orange"></v-switch>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="6" class="col">
          <label>Желаемая заработная плата</label>
          <v-text-field v-model="form.salary" variant="outlined"></v-text-field>
        </v-col>
        <v-col cols="6" class="col">
          <label>Желаемая часовая ставка</label>
          <v-text-field v-model="form.salaryPerHour" variant="outlined"></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="6" class="col">
          <label>График работы</label>
          <v-select
              clearable
              :items="['California', 'Colorado', 'Florida', 'Georgia', 'Texas', 'Wyoming']"
              variant="outlined"
              v-model="form.schedule"
          ></v-select>
        </v-col>
        <v-col cols="6" class="col">
          <label>Желаемая выработка часов</label>
          <v-text-field v-model="form.hours" variant="outlined"></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col class="col">
          <label>О себе</label>
          <v-textarea v-model="form.about" variant="outlined"></v-textarea>
          <div style="font-size: 10px; text-align: right; margin-top: -10px;">
            {{form?.about?.length || 0}}/{{500}}
          </div>
        </v-col>
      </v-row>
      <v-row>
        <v-col class="col" style="display: flex; justify-content: flex-end; margin-top: 10px;">
          <v-btn>Отмена</v-btn>
          <v-btn @click.prevent="save" color="orange" style="color: white; margin-left: 10px;">Сохранить</v-btn>
        </v-col>
      </v-row>
    </div>
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
const showCalender = ref(false)

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

const save = () => {
  const value = {
    ...form.value,
    file: chosenFile.value
  }
  console.log(value)
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
.col {
  padding-top: 0;
  padding-bottom: 0;
}
</style>
