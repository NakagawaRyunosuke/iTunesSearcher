<template>
    <div class="title">
        <h1>{{ titleText }}</h1>
    </div>
</template>

<script>
export default {
    data(){
        return{
            titleText:"iTunes Sercher"
        }
    }
}
</script>

<style scoped>
.title{
    position: fixed;
    top: 0;
    left:0;
    padding-left: 10px;
    width: 100%;
    background-color: #35495e;
    color: #fff;
}
</style>