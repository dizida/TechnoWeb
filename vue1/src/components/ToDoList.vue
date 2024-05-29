<script setup>
import {reactive} from "vue";
import Chose from "../Chose";
import ToDoListItem from "@/components/ToDoListItem.vue";

const listeC = reactive([new Chose("menage"), new Chose("Vaiselle")]);
const toto = new Chose("menage");
// console.log(listeC[0].pourAfficher()) permet d'afficher dans la console
//l'élément 0 de la liste

function handlerDelete(index) {
  listeC.splice(index, 1);
}

function handlerFaire(index) {
  listeC[index].faire();
}


</script>

<template>
  <h3>Liste des choses à faire</h3>

  <ul>
    <li v-for="(thing, index) in listeC" :key=[thing.id]>
      <ToDoListItem :chose="thing"
                    :indexChose = "index"
                    @eventDelete="handlerDelete"
                    @eventDo="handlerFaire"/>
    </li>
  </ul>

</template>

<style scoped>
h3 {
  margin: 40px 0 0;
}
</style>