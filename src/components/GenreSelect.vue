<template>
    <span>
        <span>Seleziona genere: </span>
        <select v-model="genreSelectValue" @change="$emit('genreSelected', genreSelectValue)">
            <option value="">All</option>
            <option v-for="(singleGenre, index) in genres" :key="index" :value="singleGenre">{{singleGenre}}</option>
        </select>
    </span>
</template>

<script>
export default {
    name: 'GenreSelect',
    props:{
        genres: Array
    },
    data:function(){
        return{
            genreSelectValue: ''
        }
    }
}
</script>

<style lang="scss" scoped>
select{
    padding: 5px;
    margin-right: 20px;
}
</style>