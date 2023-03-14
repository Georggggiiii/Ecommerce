<template>
  <HeaderComp />
  <router-view/>
</template>

<script>
import HeaderComp from './components/Header/HeaderComp.vue'
import store from './store/index'
export default {
  components: {
    HeaderComp
  },
  mounted () {
    if(localStorage.getItem('cartItems')) {
      store.commit('replaceProduct', JSON.parse(localStorage.getItem('cartItems')))
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
