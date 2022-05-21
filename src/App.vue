<template>
  <div>
  <HeaderComp />
  <MainComp />
  </div>
</template>

<script>
import MainComp from './components/MainComp'
import HeaderComp from './components/HeaderComp'


export default {
  name: 'App',
  components: {
   MainComp,
   HeaderComp
  }
}
</script>

<style lang="scss">

</style>
