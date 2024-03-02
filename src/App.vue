<template>
  <v-app>
    <v-main>
        <v-container fluid class="fill-height" style="padding:0; margin: 0;">
            <v-row class="fill-height" style="flex-wrap: nowrap; margin: 0;">
              <v-col cols="3" style="background: #212121; min-width: 200px; margin: 0;">
                <left-menu />
              </v-col>
              <v-col cols="9" style="min-width: 200px; padding: 0; margin: 0;">
                <top-menu />
                <v-row style="flex-wrap: nowrap; margin: 0;">
                  <v-col cols="8" style="margin: 0;">
                    <edit-profile-form />
                  </v-col>
                  <v-col cols="4" style="margin: 0;">
                    <right-menu />
                  </v-col>
                </v-row>
              </v-col>
            </v-row>
        </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
  //
import LeftMenu from "@/components/LeftMenu.vue";
  import RightMenu from "@/components/RightMenu.vue";
  import TopMenu from "@/components/TopMenu.vue";
  import EditProfileForm from "@/components/EditProfileForm.vue";
</script>
