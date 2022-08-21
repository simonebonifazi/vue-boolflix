<template>
    <ul>
        <li>
            {{ production.title || production.name }}
        </li>
        <li>
            {{ production.original_title || production.original_name }}
        </li>
        <li>
            <img v-if="hasFlag" :src="flagSource" :alt="production.original_language">
            <span v-else>
                {{ production.original_language }}
            </span>
        </li>
        <li>
            {{ production.vote_average }}
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
    computed:{
        hasFlag(){
            const flags = ['it', 'en' , 'fr' , 'es'];
            return flags.includes(this.production.original_language)
        },
        flagSource(){
            return require(`../assets/img/${this.production.original_language}.png`)
        }
    }

};
</script>

<style>

</style>