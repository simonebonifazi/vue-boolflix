<template>
    <div>
        Voto:
        <FontAwesomeIcon :icon="renderStar(n)" v-for="n in 5" :key="n" />
    </div>
</template>

<script>
export default {
    name: "StarsRate",
    props: {
        vote: Number,
    },
computed: {
        roundedUpVote() {
            return Math.ceil(this.vote / 2);
        }
},
methods:{
    renderStar(n){
        const iconType = this.vote >= n ? "fa-solid" : "fa-regular";
        return iconType + " fa-star"
    }
}
}
</script>

<style>

</style>