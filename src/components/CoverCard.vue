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
            {{ production.vote_average }}
            <!-- Add Icons using String format -->
            <font-awesome-icon icon="fa-solid fa-star"></font-awesome-icon>

        </li>
    </ul>
</template>

<script>
// https://image.thdb.org/ w342
export default {
    name: 'CoverCard',
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
        roundedUpVote(){
            let vote = this.production.vote_average;

            if(vote < 1 ) vote = 1;

            return Math.ceil(vote / 2);
        }
    }

};
</script>

<style>

</style>