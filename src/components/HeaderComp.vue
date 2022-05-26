<template>
  <div class="my-header">
    <div class="nav-section">
      <img src="../assets/img/ketflix.png" alt="">

      <ul class="d-flex">
        <li @click="returnPopular(page)">Home</li>
        <li>Movies</li>
        <li>TV series</li>
      </ul>
    </div>

    <div class="seacrh d-flex align-items-center">
    <div>
      <input 
      v-model.trim="insertTxt" 
      @keyup.enter="select(insertTxt)"   
      type="text" placeholder="Cerca">
    </div>
    <div>
      <button @click="select(insertTxt)" class="btn btn-danger k_button">Cerca</button>
      <!-- <button @click="reloadPage" class="btn btn-warning k_button" >Reload</button>  -->
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
  },
  methods:{
    // reloadPage() {
    //   window.location.reload();
    // },
    select(insertTxt){
      this.$emit('provideText', insertTxt);
      this.insertTxt = ''
    },
    returnPopular(page){
      this.$emit('goBackToHomePage', page);
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
    margin-left: 10px;
    padding: 3px;
  }
  .nav-section{
    width: 500px;
    display:flex;
    align-items: center;
    ul{
      margin: 0;
    li{
      list-style: none;
      margin-right: 20px;
      font-size: 17px;
      &:hover{
        cursor: pointer;
        color: rgb(183, 183, 183)
      }
      &:active{
        color:rgb(255, 77, 77);
      }
    }
    }
  }
}

</style>