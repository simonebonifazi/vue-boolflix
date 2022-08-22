<template>
    <main>
        <section id="films">
            <div>
                <h2> Movies</h2>
            </div>
            <CoverCard v-for="movie in movies" :key="movie.id" :production="movie" />
        </section>
        <section id="series">
            <div>
                <h2>Series</h2>
            </div>
            <CoverCard v-for="serie in series" :key="serie.id" :production="serie" />
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

<style>

</style>