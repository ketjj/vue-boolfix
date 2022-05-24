<template>
  <div class="my-main">
    <div class="k_container">

      <div>
        <h4 v-if="titleCard == 'movie'">Movie</h4>
        <h4 v-else>Tv Series</h4>

        <div class="card-wrapper">
          <CardComp
          v-for="(singleFilm,index) in itemList" :key="`film${index}`"
          :cardData="singleFilm"
          />
        </div>
      </div>

    </div>
  </div>


    
</template>

<script>
import CardComp from '@/components/CardComp'

export default {
  name: 'MainComp',
  components:{
    CardComp
  },

  props:{
    itemList:Array,
    titleCard: String

  }
}
</script>

<style lang="scss" scoped>
.my-main{
  min-height: 100vh;

  padding-top: 100px;
  color:white; 
  .k_container{
    width: 75%;
    margin: 0 auto;
  }
  h4{
  text-transform: uppercase;
  margin: 30px 0;
}
.card-wrapper{
  display: flex;
  flex-wrap: wrap;
  
}
}

    
  

</style>