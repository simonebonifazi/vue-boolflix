<template>
    <div>
        Voto:
        <!-- <font-awesome-icon icon="fas fa-star" v-for="star in roundedUpVote" :key="star" /> -->
        <i class="fa-solid fa-star" v-for="star in roundedUpVote" :key="star"></i>
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
}
}
</script>

<style>

</style>