<template>
    <div class="disk_card text-center">
        <img :src="myDisk.poster" :alt="myDisk.title">
        <h3 class="disk_title">{{myDisk.title}}</h3>
        <div class="disk_author">{{myDisk.author}}</div>
        <div class="disk_year">{{myDisk.year}}</div>
    </div>
</template>

<script>
export default {
    name:'SingleDisk',
    props:[
        'myDisk'
    ]
}
</script>

<style scoped lang="scss">
.disk_card{
    width: calc((100% / 5) - 40px);
    padding: 15px;
    margin: 10px 20px;
    background-color: #2e3a46;
    h3{
        margin: 15px 0;
        font-size: 23px;
        font-weight: bold;
    }
    .disk_author,
    .disk_year{
        color: gray;
        font-size: 19px;
        font-weight: 600;
    }
}
</style>