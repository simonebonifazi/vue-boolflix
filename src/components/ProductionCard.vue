<template>
    <ul>
        <li>
            {{ production.title || production.name }}
        </li>
        <li>
            {{ production.original_title || production.original_name }}
        </li>
        <li>
            {{ production.original_language }}
        </li>
        <li>
            {{ production.vote_average }}
        </li>
    </ul>
</template>

<script>
export default {
    name: 'ProductionCard',
    props:{
        production: Object,
    },

};
</script>

<style>

</style>