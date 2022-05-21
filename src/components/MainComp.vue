<template>
    
  <div>
    <MainCard
    v-for="(singleFilm,index) in filmlist" :key="`film${index}`"
    :film="singleFilm"
    />

  </div>
</template>

<script>
import MainCard from '@/components/MainCard'

export default {
  name: 'MainComp',
  components:{
    MainCard
  },

  props:{
    filmlist:Array
  }
}
</script>

<style>

</style>