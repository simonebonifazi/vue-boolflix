<template>
    <div class="card-cover">
        <!-- card cover -->
        <img :src="`${UriImg}${production.poster_path}`" :alt="originalTitle">
        <!-- card description -->
        <div class="card-description">
            <!-- title -->
            <h3>
                {{title}}
            </h3>
            <!-- original title -->
                <span>
                    Titolo originale:
                </span>
            <span>
                {{originalTitle}}
            </span>
            <!-- language -->
            <div>
                Lingua:
                <img v-if="hasFlag" :src="require(`./../assets/img/${production.original_language}.png`)"
                :alt="production.original_language">
            <span v-else>
                {{ production.original_language }}
            </span>
            </div>
            <!-- vote -->
            <StarsRate :vote="production.vote_average" />
        </div>
    </div>
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
        title() {
            return this.production.title || this.production.name;
        },
        originalTitle() {
            return this.production.original_title || this.production.original_name;
        },
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

<style scoped lang="scss">
.card-description img{
max-width: 35px;
}
</style>