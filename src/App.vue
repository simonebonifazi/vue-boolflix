<template>
  <div>
    <BaseHeader placeholder="Inserisci il titolo che vuoi cercare..." @start-search="startSearch" />
    <MainSection :movies="movies" :series="series" />
    
  </div>
</template>

<script>

import axios from 'axios'
import BaseHeader from './components/BaseHeader.vue'
import MainSection from './components/MainSection.vue'
export default {
  name: 'Bool-Flix',
  components: {
    BaseHeader,
    MainSection
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

<style lang="scss">



@import "~bootstrap/scss/bootstrap";
// reset
*{
  box-sizing: border-box;
  margin:0;
  padding:0;
}

body{
  background-color: #494444;
}

</style>
