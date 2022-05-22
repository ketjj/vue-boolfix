<template>
  <div>
     <h4 class="my-4">TV Series</h4>
    <div class="card-wrapper">
      <TvCard
      v-for="(singleTv,index) in seriesList" :key="`tv${index}`"
      :serie="singleTv"
      />
    </div>
  </div>
</template>

<script>
import TvCard from '@/components/TvCard'

export default {
  name: 'ShowTvComp',
  components:{TvCard},
  props:{
    seriesList:Array
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