<template>
    <div class="k_card">
      <div class="mb-4">
        <img :src="`https://image.tmdb.org/t/p/w200${film.poster_path}`" alt="film.title">
      </div>

      <div class="info">
        <div class="title">{{film.title}}</div>
        <div class="original">Original Name:</div>
        <div class="name">"{{film.original_title}}"</div>
        <div>Language:{{film.original_language}}</div>
        <div>Rating: {{film.vote_average}}</div>
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
  flex-basis: 20%;
  padding-right: 15px;
  text-align: left;
  margin-bottom: 30px;
  &:hover{
    cursor: pointer; 
    display: block;   
  }
  img{
    width:100%;
    object-fit: contain;
  }
  .info{

    width: 200px;
    padding-left: 15px;
    color: rgb(183, 180, 180);    
    //display: none;
    .overlay{
      background-color: black;
    }

    .title{
      font-size: 16px;
      text-transform: uppercase;
      font-weight: bold;
      color:white;
    }
    .original{
      font-size: 14px; 
    }
   
  }
}
</style>