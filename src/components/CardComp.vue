<template>
    <div class="k_card">
     

      <img :src="`https://image.tmdb.org/t/p/w200${cardData.poster_path}`" alt="">
      <img v-if="cardData.poster_path == undefined" src="../assets/img/default.jpg" alt="">
      
    
      <div class="info">
        <div class="more-info">
          
        <div v-if="(cardData.title || cardData.name) === (cardData.original_title || cardData.original_name)" class="title">{{cardData.title || cardData.name}}</div>

        <div v-else class="original">
          <div class="title">{{cardData.title || cardData.name}}</div>
          <div>Original Name:  {{cardData.original_title || cardData.original_name}}</div>
        </div>
        <span>Original Language: 
          <!-- <img :src="(`..assets/img/flags/en.png`)" alt=""> -->
          <img :src="require(`../assets/img/flags/${cardData.original_language}.png`)" :alt="cardData.original_language">

        </span>


        <div>Rating: 
          <i v-for="index in  Math.ceil(parseFloat(cardData.vote_average) / 2)" :key="`k-${index}`" class="fa-solid fa-star full-star"></i>
          <i v-for="index in (5 -  Math.ceil(parseFloat(cardData.vote_average) /2))" :key="`key-${index}`" class="fa-regular fa-star"></i>

        </div>
        <div class="my-2">Overview:</div>
        <div v-if="cardData.overview === ''"> Non presente</div>
        <div v-else class="overview">{{cardData.overview}} </div>
        </div>
      </div>

           

    </div>

</template>

<script>


export default {
 name: 'CardComp',
  props:{
    cardData:Object
  },
  components:{

  }
}
</script>

<style lang="scss" scoped>
.k_card{
  position: relative;
  flex-basis: 200px;
  height: 300px;
  box-shadow: 0px 0px 10px black;
  margin:0 26px 50px 0;  
    &:hover{
      //transform: scale(1.1);
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
    overflow: auto;
    .more-info{
    height:265px;
      .title{
        font-size: 14px;
        margin-bottom: 10px;
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
      img{
        width:20px;
      } 

    }
  }

</style>