<template>
    <div class="card-cover ">
        <!-- card cover -->
        <img class="cover pe-4 " v-if="production.poster_path === null" src="../assets/img/preview-not-find.png"
            alt="unavaible-poster">
        <img class="cover pe-4" v-else :src="`${UriImg}${production.poster_path}`" :alt="originalTitle">
        <!-- card description -->
        <div class="card-description text-center">
            <!-- title -->
            <h5>
                {{title}}
            </h5>
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
            <!-- overview -->
            <div v-if="production.overview">
                Overview: {{production.overview }}
            </div>
            <div v-else>
                Overview: Not Found
            </div>
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
height: 20px;
}

.card-cover>img{
    max-width: 342px;
}

.card-cover{
    position: relative;
    .cover{
        object-fit: cover;
        transition: opacity 0.3s;
    }
    &:hover{
        .cover{
            opacity: 0.1;
        }
        .card-description{
            opacity: 1;
        }
    }

    .card-description{
        position: absolute;
        top:0;
        bottom:0;
        left:0;
        right:0;

        padding: 8px;

        overflow: auto;

        opacity: 0;
    }
}

</style>