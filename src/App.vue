<template>
  <div class="my-app">
  <HeaderComp @provideText='getInsertedText'/>

  <MainComp v-if=" movieLists.length > 0" titleCard="movie"
  :itemList="filteredFilmData" 
  />

   <MainComp v-if=" tvLists.length > 0" titleCard="tv-series"
  :itemList="filteredTvData"
  />

  <h3 v-if="(movieLists.length === 0) && (tvLists.length === 0)">
    Nessuna informazione è stata trovata 
  </h3>
  

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
        //console.log(res.data.results, '------------')
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
         //console.log(res.data.results, '=======')
         this.tvLists = res.data.results; 
         this.insertedText = ''           
      })
      .catch(err =>{
        console.log(err)
      })
    },

    getPopularNow(){
      const params = {
        api_key: this.api_key
      }

      axios.get(`https://api.themoviedb.org/3/movie/popular`,{ params })
        .then((response) => {
          for(let i = 0; i < 10; i++) {
        this.movieLists.push(response.data.results[i])
      }
        });
      axios
        .get(`https://api.themoviedb.org/3/tv/popular`, { params })
        .then((response) => {
          for(let i = 0; i < 10; i++) {
        this. tvLists.push(response.data.results[i])
      }
        });

    },

    getInsertedText(inputText){
      this.insertedText = inputText;
      this.getApiFilm();
      this.getApiTv();    
    }  
  },

  computed:{
    filteredFilmData: function() {
      //console.log("chiamata");
      return this.movieLists;         
    },
    filteredTvData: function() {
      //console.log("chiamata");
      return this.tvLists;         
    }
  },
  mounted(){
    this.getPopularNow()
  }  
}
</script>

<style lang="scss">
@import './assets/style/general';
.my-app{
  background-color: #242832;
  min-height: 100vh;
  color: white;
  h3{
    padding-top: 100px;
    width: 75%;
    margin: 0 auto;
  }
}

</style>
