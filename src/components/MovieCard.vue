<template>
    <div class="k_card">
      
      <img :src="`https://image.tmdb.org/t/p/w200${film.poster_path}`" alt="film.title">
     

      <div class="info">
        <div class="title">{{film.title}}</div>
        <div class="or-line"></div>
        <div class="original">Original Name:</div>
        <div class="name">"{{film.original_title}}"</div>
        <div>Language:{{film.original_language}}</div>
        <div>Rating: {{film.vote_average}} <i class="fa-solid fa-star"></i></div>
      </div>

    </div>

</template>

<script>
export default {
 name: 'MovieCard',
  props:{
    film:Object
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
  }

</style>