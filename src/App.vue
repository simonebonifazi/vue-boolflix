<template>
  <div>
    <SearchBar placeholder="Inserisci il titolo che vuoi cercare..." @search="startSearch" />
    <!-- film section -->
    <section id="movies">
      <h3>Films</h3>
      <ProductionCard v-for="movie in movies" :key="movie.id" :production="movie" />  
    </section>
    <!-- series section -->
    <section id="series">
      <h3>Series</h3>
      <ProductionCard v-for="serie in series" :key="serie.id" :production="serie" />
    </section>
  </div>
</template>

<script>

import axios from 'axios'
import SearchBar from './components/SearchBar.vue'
import ProductionCard from './components/ProductionCard.vue'
export default {
  name: 'Bool-Flix',
  components: {
    SearchBar,
    ProductionCard,
},
data(){
  return{
    movies: [],
    series: [],
    api: {
      language: "it-IT",
      key: "963061c4be5e09116f528b4d6f430660",
      baseUri: "https://api.themoviedb.org/3",
   }     
  }
},

methods:{
  startSearch(query){
//check
    if(!query){
      this.movies= this.series= [];
      return
    } 
    const {language, key} = this.api;
    const config = {
      params: {
        api_key: key,
        language,
        query,
      },
    };

    this.fetchData('/search/movie', config, 'movies');
    this.fetchData('/search/tv', config, 'series');

  },
  
  fetchData(endpoint, config, target){
    axios.get(`${this.api.baseUri}${endpoint}`, config)
      .then((res) => {
        this[target] = res.data.results;
      });

  },
}
  
}
</script>

<style >

</style>
