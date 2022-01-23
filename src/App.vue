<template>
  <div class="root">
    <Navi/>
    <Search class="search" @loadStart="onLoadStart" @loadComplete="onLoadComplete"/>
    <Result :items="items" :loadProgress="loadProgress" :result="result"/>
  </div>
</template>

<script>
import Search from "@/components/Search";
import Result from "@/components/Result";
import Navi from "@/components/Navi";

export default{
  data(){
    return{
      items:[],
      loadProgress:false,
      result:""
    }
  },
  methods:{
    onLoadStart(){
      this.loadProgress = true;
    },
    onLoadComplete({ results }){
      this.items = results;
      if(results.length == 0) this.result = "お探しのコンテンツはございません、申し訳ありません。orz";
      else this.result = ""

      this.loadProgress = false;
    }
  },
  components:{
    Search,
    Result,
    Navi
  }
}
</script>

<style scoped>
.root{
  padding-top:70px;
}
.search{
  width:100%;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 1;
}
</style>

<style>
html{
  font-size: 62.5%;
}
body{
  margin: 0;
  color: #35495e;
}
p{
  margin: 0;
}
ul{
  padding: 0;
  margin: 0;
}
</style>
