<template>
    <section>
        <div class="container">
            <GenreSelect @genreSelected="changeValue" />
            <div class="disks_container">
                <SingleDisk v-for="(disk,index) in filterGenre()" :key="index" :myDisk="disk" />
            </div>
        </div>
    </section>
</template>

<script>
import axios from 'axios'
import SingleDisk from './SingleDisk.vue'
import GenreSelect from './GenreSelect.vue'

export default {
    name: 'Disks',
    components:{
        SingleDisk,
        GenreSelect
    },
    data:function(){
        return{
            disksList: [],
            newValue:''
        }
    },
    methods:{
        changeValue: function(userGenre){
            this.newValue = userGenre
        },
        filterGenre: function(){
            if(this.newValue.length == 0){
                return this.disksList
            }
            const filteredArray = this.disksList.filter((element) => {
                return element.genre.toLowerCase().includes(this.newValue.toLowerCase())
            })
            return filteredArray
        }
    },
    created: function(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) =>{
            this.disksList = response.data.response
        })
    }
}
</script>

<style scoped lang="scss">
.disks_container{
    display: flex;
    flex-wrap: wrap;
}
</style>