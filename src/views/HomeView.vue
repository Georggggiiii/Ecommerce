<template>
  <div class="input">
    <input type="text" placeholder="Search..." v-model="search">
  </div>
  <div class="home">
    <ProductComp v-for="(item, index) in getData" :key="index" :data="item" />
  </div>
</template>

<script>
import ProductComp from '@/components/ProductComp.vue'
import prData from '../Products.json'

export default {
  name: 'HomeView',
  data() {
    return {
      productsData: prData,
      search: ''
    }
  },
  components: {
    ProductComp
  },
  computed: {
    getData() {
      return this.productsData.filter(el => el.title.toLowerCase().includes(this.search.toLowerCase()))
    }
  }
}
</script>
<style scoped>
.input {
  text-align:center;
  margin-top:50px;
}
.input input {
  padding:10px 16px;
  outline:none;
  border-radius:10px;
  border:1px solid orange;
}
.home {
  margin-top:20px;
 flex-wrap:wrap;
 display:flex;
  justify-content: center;
}
</style>