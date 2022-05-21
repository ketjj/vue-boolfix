<template>
    <div class="k_card">
      <img :src="`https://image.tmdb.org/t/p/w200${film.poster_path}`" alt="film.title">

      <div>{{film.title}}</div>
      <div>{{film.original_title}}</div>
      <div>{{film.original_language}}</div>
      <div>{{film.vote_average}}</div>

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
  text-align: center;
  img{
    width:100%;
  }
}
// .card-container{
//     width: 100%;
//     height: 100%;
//     display: flex;
//     flex-basis: 25%;
//     flex-direction: column;
//     justify-content: center;
//     align-items: center;
//     .image-wrap{
//       width: 20%;
//     }
//     img{
//       width: 100px;
//     }
    
//     }

</style>