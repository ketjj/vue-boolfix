<template>
    <div class="k_card">
      <div class="mb-4">
        <img :src="`https://image.tmdb.org/t/p/w200${serie.poster_path}`" alt="serie.name">
      </div>

       <div class="info">
        <div class="title">{{serie.name}}</div>
        <div class="original">Original Name:</div>
        <div class="name">"{{serie.original_name}}"</div>
        <div>Language: {{serie.original_language}}</div>
        <div>Rating: {{serie.vote_average}}</div>
      </div>

    </div>

</template>



<script>
export default {
 name: 'TvCard',
  props:{
    serie:Object
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