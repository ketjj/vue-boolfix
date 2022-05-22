<template>
  <div>
  <HeaderComp @provideText='getInsertedText'/>
  <MainComp :filmlist="filteredFilmData"/>
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

       insertedText: 'star wars',

       apiUrlFilm: 'https://api.themoviedb.org/3/search/movie',
       api_key: 'db434741c3c9df5b6b054b9b08d39df2',
       language: 'it_IT',

       movieLists: [],      
     }
   },

  methods: {
    getApiFilm(){
      const apiParametres = {
         api_key: this.api_key,
         language: this.language,
         query: this.insertedText
       };
      axios.get(this.apiUrlFilm, {params: apiParametres})
      .then(res =>{
        console.log(res.data.results, '------------')
        this.movieLists = res.data.results;            
      })
    },

    getInsertedText(inputText){
      this.insertedText = inputText;
    }  
  },
  computed:{
    filteredFilmData: function() {
       if(this.insertedText == ''){
         return  this.movieLists;
       } else{
         this.getApiFilm();
         //return this.movieLists.filter((movie) => movie.title.toLowerCase().includes(this.insertedText.toLowerCase()));
         return this.movieLists;

       }
    },
    // filteredTvData: function() {
    //    if(this.insertedText == ''){
    //      return  this.movieLists;
    //    } else{
    //      this.getApi();
    //      return this.movieLists.filter((movie) => movie.title.toLowerCase().includes(this.insertedText.toLowerCase()));
    //    }
    // }
  
  } 

  
}
</script>

<style lang="scss">
@import './assets/style/general';

.div{
  min-height: 100vh;
  background-color: #242832;
}

</style>
