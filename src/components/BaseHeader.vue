<template>
  <header>
    <div class="container h-100">
        <div id="navbar" class="h-100 d-flex justify-content-between align-items-center">
         <h1 class="text-danger"> BoolFlix</h1>
         <div class="d-flex justify-content-center aling-items-center">
            <SearchBar @search="startSearch" />
         </div>   
        </div>
    </div>
  </header>
</template>

<script>

import SearchBar from "./SearchBar.vue";
export default {
name: "BaseHeader",
components: {
    SearchBar,
},
methods:{
    startSearch(term){
        this.$emit("start-search", term)
    }
}
}
</script>

<style lang="scss">
</style>