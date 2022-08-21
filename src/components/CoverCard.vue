<template>
    <ul>
        <li>
            {{ production.title || production.name }}
        </li>
        <li>
            {{ production.original_title || production.original_name }}
        </li>
        <li>
            <img v-if="hasFlag" :src="`${UriImg}${production.poster_path}`" :alt="production.original_language">
            <span v-else>
                {{ production.original_language }}
            </span>
        </li>
        <li>
            <StarsRate :vote="production.vote_average"/> 
        </li>
    </ul>
</template>

<script>
import StarsRate from "./StarsRate.vue"
export default {
    name: 'CoverCard',
    components: {StarsRate},
    props:{
        production: Object,
    },
    data(){
        return{
            UriImg: "https://image.tmdb.org/t/p/w342"
        };
    },
    computed:{
        hasFlag(){
            const flags = ['it', 'en' , 'fr' , 'es'];
            return flags.includes(this.production.original_language)
        },
        flagSource(){
            return require(`../assets/img/${this.production.original_language}.png`)
        },
       
    }

};
</script>

<style>

</style>