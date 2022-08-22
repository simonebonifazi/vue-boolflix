<template>
    <main class="container">
        <section id="films">
            <h2 class="mb-3"> Film</h2>
            <div class="d-flex">

                <CoverCard v-for="movie in movies" :key="movie.id" :production="movie" />
            </div>
        </section>
        <section class="mb-3" id="series">
            <h2>Serie TV</h2>
            <div class="d-flex">

                <CoverCard v-for="serie in series" :key="serie.id" :production="serie" />
            </div>
        </section>
    </main>
</template>

<script>
import CoverCard from "./CoverCard.vue"
export default {
name:"MainSection",
components:{
    CoverCard,
},
props:{
movies: Array,
series: Array
}
}
</script>

<style lang="scss" scoped>
main{
    
    padding-top: 100px;
    
}
</style>