<template>
    <section>
        <div class="container">
            <div class="disks_container">
                <SingleDisk v-for="(disk,index) in disksList" :key="index" :myDisk="disk" />
            </div>
        </div>
    </section>
</template>

<script>
import axios from 'axios'
import SingleDisk from './SingleDisk.vue'

export default {
    name: 'Disks',
    components:{
        SingleDisk
    },
    data:function(){
        return{
            disksList: []
        }
    },
    created: function(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) =>{
            console.log(response.data)
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