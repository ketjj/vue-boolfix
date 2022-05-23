<template>
  <div class="my-header">
    <div>
      <img src="../assets/img/ketflix.png" alt="">
    </div>

    <div class="seacrh d-flex align-items-center">
    <div>
      <input 
      v-model.trim="insertTxt" 
      @keyup.enter="$emit('provideText', insertTxt)"   
      type="text" placeholder="Cerca">
    </div>
    <div>
      <button @click="$emit('provideText', insertTxt)" class="btn btn-danger k_button">Cerca</button>
    </div>

    </div>
    
  </div>
</template>

<script>

export default {
  name: 'HeaderComp',
  data(){
    return{
      insertTxt:''
    }
  }
}
</script>

<style lang="scss" scoped>
.my-header{
  position: fixed;
  z-index: 999;
  width: 100%;
  height: 68px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 15px;
  background-image: linear-gradient(rgba(0,0,0,.7) 10%,rgba(0,0,0,.1));
  color: white;
  img{
    width: 120px;
  }
  .k_button{
    width: 80px;
    margin: 10px;
    padding: 3px;
  }
}

</style>