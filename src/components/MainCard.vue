<template>
  <div class="card">
    <div>
      <img :src="`https://image.tmdb.org/t/p/w500${film.poster_path}`" alt="film.title">
    </div>
    <div>{{film.title}}</div>
    <div>{{film.original_title}}</div>
    <div>{{film.original_language}}</div>
    <div>{{film.vote_average}}</div>

  </div>
</template>

<script>
export default {
 name: 'MainCard',
  props:{
    film:Object
  }
}
</script>

<style>

</style>