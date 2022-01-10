<template>
    <span>
        <span>Seleziona genere: </span>
        <select v-model="genreSelectValue" @change="$emit('genreSelected', genreSelectValue)">
            <option value="">All</option>
            <option value="Rock">Rock</option>
            <option value="Jazz">Jazz</option>
            <option value="Metal">Metal</option>
            <option value="Pop">Pop</option>
        </select>
    </span>
</template>

<script>
export default {
    name: 'GenreSelect',
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