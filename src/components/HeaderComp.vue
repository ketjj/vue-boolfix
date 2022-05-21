<template>
  <div>HEADER
    <ShowTvComp/>
    <ShowMovieComp/>
  </div>
</template>

<script>
import ShowTvComp from '@/components/ShowTvComp'
import ShowMovieComp from '@/components/ShowMovieComp'

export default {
  name: 'HeaderComp',
  components:{
    ShowTvComp,
    ShowMovieComp
  }

}
</script>

<style>

</style>