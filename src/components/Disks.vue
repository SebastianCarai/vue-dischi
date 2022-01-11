<template>
    <section>
        <div class="container">
            <GenreSelect :genres="genresArray" @genreSelected="changeGenreValue" />
            <ArtistSelect @artistSelected="changeArtistValue" />
            <div class="disks_container">
                <SingleDisk v-for="(disk,index) in filterSelection()" :key="index" :myDisk="disk" />
            </div>
        </div>
    </section>
</template>

<script>
import axios from 'axios'
import SingleDisk from './SingleDisk.vue'
import GenreSelect from './GenreSelect.vue'
import ArtistSelect from './ArtistSelect.vue'

export default {
    name: 'Disks',
    components:{
        SingleDisk,
        GenreSelect,
        ArtistSelect
    },
    data:function(){
        return{
            disksList: [],
            genresArray: [],
            newGenrevalue:'',
            newArtistValue: ''
        }
    },
    methods:{
        changeGenreValue: function(userGenre){
            this.newGenrevalue = userGenre
        },
        changeArtistValue: function(userArtist){
            this.newArtistValue = userArtist  
        },
        filterSelection: function(){
            if(this.newGenrevalue.length == 0 && this.newArtistValue.length == 0){
                return this.disksList
            }
            const filteredArray = this.disksList.filter((element) => {
                return (element.author.toLowerCase().includes(this.newArtistValue.toLowerCase()) && element.genre.toLowerCase().includes(this.newGenrevalue.toLowerCase()))
            })
            return filteredArray
        }
    },
    created: function(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) =>{
            this.disksList = response.data.response;

            this.disksList.forEach((element) =>{
            if (!this.genresArray.includes(element.genre)){
                    this.genresArray.push(element.genre)
                }
            })
        });
    }
}
</script>

<style scoped lang="scss">
.disks_container{
    display: flex;
    flex-wrap: wrap;
}
</style>