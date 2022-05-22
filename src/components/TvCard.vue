<template>
    <div class="k_card">
      <img :src="`https://image.tmdb.org/t/p/w200${serie.poster_path}`" alt="serie.name">

      <div>{{serie.name}}</div>
      <div>{{serie.original_name}}</div>
      <div>{{serie.original_language}}</div>
      <div>{{serie.vote_average}}</div> 

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
  text-align: center;
  img{
    width:100%;
  }
}
</style>