<template>
  <v-container>
    Recherche de Films
  </v-container>
  <FormText @update="update"></FormText>
  <FilmAffichList :pcritere = "critere"></FilmAffichList>
</template>

<script setup>
import FilmAffichList from "@/components/FilmAffichList.vue";
import FormText from "@/components/FormText.vue";
import {ref} from "vue";

let critere = ref("")

function update(value) {
  critere.value = value
}
</script>
