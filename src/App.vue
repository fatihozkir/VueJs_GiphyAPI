<template>
  <div id="app">
    
    <search v-on:SearchRequested="handleSearch"></search>
    <p v-if="isLoading">Loading...</p>
    <preview :gifs=gifs></preview>
  </div>
</template>

<script>
import Search from './components/search.vue'
import Preview from './components/Preview.vue'
export default {
  name: 'app',
  components:{Search,Preview},
  data(){
    return {
      isLoading:true,
      gifs:[]
    }
  },
  methods:{
    doQuery(url){
    fetch(url).then((res)=>{return res.json()}).then((res)=>{this.gifs=res.data});
    this.isLoading=false;
    },
    handleSearch(query)
    {
      this.gifs=[];
      this.isLoading=true;
      const query1='https://api.giphy.com/v1/gifs/search?api_key=RJI4oOB2i4b0BbFewZtCbpqE04NJ0NZg&q='+query+'&limit=25&offset=0&rating=R&lang=en';
      this.doQuery(query1);
    
    }
  }
  ,
  created(){
    const query='https://api.giphy.com/v1/gifs/trending?api_key=RJI4oOB2i4b0BbFewZtCbpqE04NJ0NZg&limit=70&rating=G';
      this.doQuery(query);
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
