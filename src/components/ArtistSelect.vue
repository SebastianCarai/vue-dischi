<template>
    <span>
        <span>Seleziona Artista: </span>
        <select v-model="artistSelectValue" @change="$emit('artistSelected', artistSelectValue)">
            <option value="">All</option>
            <option value="Bon Jovi">Bon Jovi</option>
            <option value="Queen">Queen</option>
            <option value="Sting">Sting</option>
            <option value="Steve Gadd Band">Steve Gadd Band</option>
            <option value="Iron Maiden">Iron Maiden</option>
            <option value="Eric Clapton">Eric Clapton</option>
            <option value="Deep Purple">Deep Purple</option>
            <option value="Metallica">Metallica</option>
            <option value="Dave Weckl">Dave Weckl</option>
            <option value="Michael Jacjson">Michael Jacjson</option>
        </select>
    </span>
</template>

<script>
export default {
    name: 'ArtistSelect',
    data:function(){
        return{
            artistSelectValue: ''
        }
    }
}
</script>

<style lang="scss" scoped>
select{
    padding: 5px;
}
</style>