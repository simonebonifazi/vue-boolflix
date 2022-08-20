<template>
  <div >
  <SearchBar placeholder="Inserisci il titolo che vuoi cercare..." @search="fetchMovies"/>
  <section id="movies">
    <h3>Films</h3>
    <ul v-for="movie in movies" :key="movie.id">
    <li>
      {{movie.title}}
      {{movie.original_title}}
      {{movie.original_language}}
      {{movie.vote_avarege}}
    </li>
    </ul>
  </section>
  </div>
</template>

<script>

import axios from 'axios'
import SearchBar from './components/SearchBar.vue'
export default {
  name: 'Bool-Flix',
  components: {
    SearchBar
},
data(){
  return{
    movies: [],
    api: {
      language: "it-IT",
      key: "963061c4be5e09116f528b4d6f430660",
      baseUri: "https://api.themoviedb.org/3",
   }     
  }
},
methods:{
  fetchMovies(query){
    //api's calls

    const {language, key, baseUri} = this.api;

    const config = {
      params: {
        api_key: key,
        language,
        query
      }
    };

    axios.get(`${baseUri}/search/movie`, config)
    .then((res)=>{
      this.movies = res.data.results;
    })
  }
}
  
}
</script>

<style >

</style>
