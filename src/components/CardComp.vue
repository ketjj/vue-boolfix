<template>
    <div class="k_card">
           
      <img :src="`https://image.tmdb.org/t/p/w200${cardData.poster_path}`" alt="">
      <img v-if="cardData.poster_path == undefined" src="../assets/img/default.jpg" alt="cardData.title">
      
     
      <div class="info">
        <div class="title">{{cardData.title || cardData.name}}</div>
        <div class="or-line"></div>
        <div class="original">Original Name:</div>
        <div class="name">"{{cardData.original_title || cardData.original_name}}"</div>
        <div>Original Language: 
    
        
          <span><lang-flag :iso="cardData.original_language" :title="cardData.original_language"/></span>
        </div>


        <div>Rating: 
          <i v-for="index in  Math.ceil(parseFloat(cardData.vote_average) / 2)" :key="index" class="fa-solid fa-star full-star"></i>
          <i v-for="index in (5 -  Math.ceil(parseFloat(cardData.vote_average) /2))" :key="index" class="fa-regular fa-star"></i>

        </div>
      </div>

    </div>

</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
 name: 'CardComp',
  props:{
    cardData:Object
  },
  components:{
    LangFlag
  }
}
</script>

<style lang="scss" scoped>
.k_card{
  position: relative;
  flex-basis: 200px;
  //height: 300px;
  //overflow: hidden;
  box-shadow: 0px 0px 10px black;
  margin:0 26px 50px 0;  
    &:hover{
      transform: scale(1.1);
      box-shadow: 0px 0px 20px rgb(0, 0, 0);
      cursor: pointer;
      transition: all .7s;      
    }
    &:Hover .info{
      display: block;
    }
  }
  img{
    width:100%;
    object-fit: contain;
  }
  .info{
    position: absolute;
    z-index: 999;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100%;
    padding: 15px;
    font-size: 0.9rem;
    color: rgb(238, 226, 226);
    background-color: rgba(0, 0, 0, 0.7);
    display: none;
    .title{
      font-size: 16px;
      text-transform: uppercase;
      font-weight: bold;
      color:white;
      //border-bottom: 1px solid white;
    }
    .or-line{
      width: 30px;
      height:1px;
      background-color:rgb(242, 134, 134);
      margin: 10px 0;
      border-radius: 10px;
    }
    .original{
      font-size: 14px; 
    }
    .full-star{
      color: yellow;
    }   
  }

</style>