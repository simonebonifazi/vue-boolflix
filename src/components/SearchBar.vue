<template>
    <div class="d-flex align-items-center">
        <input type="text" :placeholder="placeholder" v-model.trim="term" class="form-control rounded mx-2">
        <button type="button" class="btn btn-outline-danger rounded" @click="$emit('search', term)">
            Cerca
        </button>
    </div>
</template>

<script>
export default {
name: "SearchBar",
props:{
    placeholder: {
        type: String,
        required: false,
        default: "Cerca tra film e serie tv..."
    },
    buttonText: {
        type: String,
        required:false,
        default: "Cerca"
    }
},
data(){
    return{
        term: ""
    }
}
}
</script>

<style lang="scss" scoped>
button{
    height: 100%;
    width: 60px;
    border-radius: 5px;
}
</style>