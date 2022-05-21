<template>
  <div class="my-main">
    <div class="k_container">

      <ShowMovieComp :onlyFilmList="filmlist"
      />

    </div>

    </div>


    
</template>

<script>
import ShowMovieComp from '@/components/ShowMovieComp'

export default {
  name: 'MainComp',
  components:{
    ShowMovieComp
  },

  props:{
    filmlist:Array
  }
}
</script>

<style lang="scss" scoped>
.my-main{
  min-height: 100vh;
  background-color: #242832;
  padding-top: 100px;
  color:white; 
  .k_container{
    width: 75%;
    margin: 0 auto;
  }
}

    
  

</style>