<template>
  <div>
  <HeaderComp @provideText='doSearch'/>
  <MainComp :filmlist="filteredList"/>
  </div>
</template>

<script>
import MainComp from './components/MainComp'
import HeaderComp from './components/HeaderComp'

import axios from 'axios'


export default {
  name: 'App',
  components: {
   MainComp,
   HeaderComp
  },
   data(){
     return{
       apiUrl: 'https://api.themoviedb.org/3/search/movie',
       apiParametres:{
         api_key: 'db434741c3c9df5b6b054b9b08d39df2',
         language: 'it_IT',
         query: 'star wars'
       },
       movieLists: [],
       filteredList: []
      
     }
   },
  mounted(){
    this.getApi()
  },
  methods: {
    getApi(){
      axios.get(this.apiUrl, {params: this.apiParametres})
      .then(res =>{
        console.log(res.data.results, '------------')
        this.movieLists = res.data.results;
        this.filteredList = this.movieLists;
            
      })
    },   
    doSearch(inputText){
      if(inputText == ''){
        this.filteredList = this.movieLists
      } else{
        this.filteredList = this.movieLists.filter((movie) => movie.title.toLowerCase().includes(inputText.toLowerCase()))
      }
    }  
  }, 
}
</script>

<style lang="scss">
@import './assets/style/general';

.div{
  min-height: 100vh;
  background-color: #242832;
}

</style>
