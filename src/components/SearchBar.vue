<template>
  <div>
    <input type="text" :placeholder="placeholder" v-model.trim="term">
    <button type="button" @click="$emit('search', term)"> 
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
        default: "Cerca"
    },
    buttonText: {
        type: String,
        required:false,
        default: "cerca"
    }
},
data(){
    return{
        term: ""
    }
}
}
</script>

<style>

</style>