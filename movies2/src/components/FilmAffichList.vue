<script setup>
import {onMounted, reactive, watch} from "vue";
import Film from '../Film';
let props = defineProps(["pcritere"]);

const apiKey = "af1e1c8f8ad6efb5b326eabaffa38b8a"
const url =
  "https://api.themoviedb.org/3/search/movie?api_key=" +
  apiKey +
  "&language=fr-FR&page=1&query="

// le state
const listeFilms = reactive([]);

onMounted(() => {
  searchFilms();
});

//la liste des films s’actualise à chaque fois que
// l’on change le paramètre (la props)
watch(props, (newcritere) => {
  console.log(newcritere.pcritere)
  searchFilms()
});

function searchFilms() {
  const fetchOptions = {method: "GET"};

  fetch(url + props.pcritere, fetchOptions)
    .then((response) => {
      return response.json();
    })
    .then((dataJSON) => {
      console.log(dataJSON);
      //clear
      listeFilms.splice(0, listeFilms.length);

      // Remplir le state avec les films en utilisant la
      // classe Film
      dataJSON.results.forEach(film => {
        // Créer une nouvelle instance de la classe Film
        // pour chaque film et l'ajouter à la listeFilms
        listeFilms.push(new Film(film));
      });
    })
    .catch((error) => {
      console.log(error);
    });




}
</script>

<template>
  <h3>Liste des films</h3>

  <v-container>
    <v-row dense>
      <v-col
        v-for="film in listeFilms"
        :key="film.id"
        cols="12"
        sm="6"
        md="3"
        lg="2"
        xl="2"
      >
        <v-card color="primary">
          <v-img
            :src="'https://image.tmdb.org/t/p/w500/' + film.affiche"
            height="300px"
            class="image"
            cover
          ></v-img>
          <v-card-title>
            {{ film.titre }}
          </v-card-title>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped>
.image {
  width: 200px;
  height: 300px;
}
</style>
