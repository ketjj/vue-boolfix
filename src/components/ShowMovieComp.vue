<template>
  <div>
     <h4 class="my-4">Movies</h4>
    <div class="card-wrapper">
      <MovieCard
      v-for="(singleFilm,index) in onlyFilmList" :key="`film${index}`"
      :film="singleFilm"
      />
    </div>
  </div>
</template>

<script>
import MovieCard from '@/components/MovieCard'

export default {
 name: 'ShowMovieComp',
 components:{MovieCard},
  props:{
    onlyFilmList:Array
  }
}
</script>

<style lang="scss" scoped>
h4{
  text-transform: uppercase;
}
.card-wrapper{
  display: flex;
  flex-wrap: wrap;
  
}
</style>