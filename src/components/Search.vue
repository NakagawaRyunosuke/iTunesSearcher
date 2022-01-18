<template>
    <div>
        <div class="container">
            <input class="text" type="text" v-model="term" @keyup.enter="exe">
            <select class="genre" name="genre" @change="onChange">
                <option value="all">all</option>
                <option value="movie">movie</option>
                <option value="podcast">podcast</option>
                <option value="music">music</option>
                <option value="musicVideo">musicVideo</option>
                <option value="audiobook">audiobook</option>
                <option value="tvShow">tvShow</option>
                <option value="software">software</option>
                <option value="ebook">ebook</option>
            </select>
            <input class="submit" type="submit" value="検索" @click="exe">
        </div>
    </div>
</template>

<script>
import axios from "axios";

export default{
    data(){
        return{
            term:"",
            currentSelect:""
        }
    },
    methods:{
        onChange(e){
            this.currentSelect = e.target.value;
        },
        async exe(){
            this.$emit("loadStart")
            const {data} = await axios.get(`https://itunes.apple.com/search?term=${this.term}&country=jp&media=${this.currentSelect}&lang=ja_jp`)
            this.$emit("loadComplete",{results:data.results})
        }
    }
}
</script>

<style scoped>
.container{
    display:flex;
    justify-content: center;
    height: 70px;
    padding: 20px;
    background-color: #35495e;
    box-sizing: border-box;
}
.text{
    width: 50%;
    max-width: 300px;
    padding: .5em;
    border: none;
}
.genre{
    margin-left: 10px;
}
.submit{
    padding:  .5em 2em;
    margin-left: 10px;
    color: #fff;
    background-color: #42b883;
    border: none;
    border-radius: 20px;
}
</style>
