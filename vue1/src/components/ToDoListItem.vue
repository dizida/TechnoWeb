<script setup>
// Définition d'une prop appelée 'chose' que ce composant attend de son parent
defineProps(["chose"], ["indexChose"] );
</script>

<template>
  <!-- Affiche le résultat de la méthode pourAfficher() de l'objet 'chose' -->
  <li>{{ chose.pourAfficher() }}

<!--    <button @click="handlerDelete(index)">delete</button>-->
    <button @click="$emit('eventDelete', indexChose)">delete</button>

<!--    <button @click="handlerFaire(index)">toDo</button>-->
    <button @click="$emit('eventDo', indexChose)">toDo</button>

  </li>

</template>

<style>

</style>