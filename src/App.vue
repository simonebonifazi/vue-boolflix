<template>
  <div>
    <SearchBar placeholder="Inserisci il titolo che vuoi cercare..." @search="startSearch" />
    <ProductionCard v-for="movie in movies" :key="movie.id" :production="movie" />
    <!-- film section -->
    <section id="movies">
      <h3>Films</h3>
      <!-- <ul>
        <li>
          {{movie.title}}
        </li>
        <li>
          {{movie.original_title}}
        </li>
        <li>
          {{movie.original_language}}
        </li>
        <li>
          {{movie.vote_avarage}}
        </li>
      </ul> -->
    </section>
    <!-- series section -->
    <section id="series">
      <h3>Series</h3>
      <ProductionCard v-for="serie in series" :key="serie.id" :production="serie" />
        <!-- <li>
          {{serie.name}}
        </li>
        <li>

          {{serie.original_name}}
        </li>
        <li>

          {{serie.original_language}}
        </li>
        <li>

          {{serie.vote_avarage}}
        </li> -->

    
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

//check the query
    if(!query){
      this.movies= this.series= [];
      return
    }
    

    //api's calls

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
