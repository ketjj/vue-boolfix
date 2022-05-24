<template>
  <div>
  <HeaderComp @provideText='getInsertedText'/>

  <MainComp titleCard="movie"
  :itemList="filteredFilmData" 
  />

   <MainComp titleCard="tv-series"
  :itemList="filteredTvData"
  />
  

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
       apiUrlTv: 'https://api.themoviedb.org/3/search/tv',
       

       api_key: 'db434741c3c9df5b6b054b9b08d39df2',
       language: 'it_IT',

       movieLists: [],  
       tvLists: [], 
       cardTitle: ['movie', 'tv-Series']  
       
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
      .catch(err =>{
        console.log(err)
      })
      //this.getApiTv()
    },

    getApiTv(){
       const apiParametres2 = {
          api_key: this.api_key,
          language: this.language,
          query: this.insertedText
        };
       axios.get(this.apiUrlTv, {params: apiParametres2})
       .then(res =>{
         console.log(res.data.results, '=======')
         this.tvLists = res.data.results;            
      })
      .catch(err =>{
        console.log(err)
      })
    },

    getInsertedText(inputText){
      this.insertedText = inputText;
      this.getApiFilm();
      this.getApiTv();    
    }  
  },

  computed:{
    filteredFilmData: function() {
      console.log("chiamata");
      return this.movieLists;         
    },
    filteredTvData: function() {
      console.log("chiamata");
      return this.tvLists;         
    }
  },
  mounted(){
    this.getApiFilm(); 
    this.getApiTv();
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
