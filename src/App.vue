<template>
  <div>
  <HeaderComp />
  <MainComp :filmlist="movieLists"/>
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
         query: 'matrix'
       },
       movieLists: [],
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
        
      })
    }
  }
}
</script>

<style lang="scss">

</style>
