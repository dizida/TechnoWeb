<script setup>
import { ref, defineProps} from 'vue';

// Définition de la variable reactive pour stocker le critère de recherche
const props = defineProps(["pcritere"]); // Définition de la prop "pcritere" provenant du parent
const critere = ref(props.pcritere); // Création d'une référence réactive pour stocker le critère de recherche
const emit = defineEmits(["update"])
// Méthode appelée lorsque le formulaire est soumis

const submitForm = () => {
  // Émettre un événement contenant le critère de recherche
  emit("update", critere.value);
};
</script>

<template>
  <!-- Formulaire de saisie du critère de recherche -->
  <form @submit.prevent="submitForm">
    <!-- Champ de texte lié au modèle critere -->
    <v-text-field
      v-model="critere"
      label="Critère de recherche"
      outlined
    ></v-text-field>
    <!-- Bouton de soumission du formulaire -->
    <v-btn type="submit">Rechercher</v-btn>
  </form>
</template>

<style scoped>

</style>
