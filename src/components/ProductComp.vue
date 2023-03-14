<template>
  <div class="product">
    <div class="product-desc">
      <img :src="data.url" alt=""  @click="openInner">
    <p class="product-name">{{ data.title }}</p>
    <div class="price">
    <p>{{ data.price}}$</p>
    </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      data: {
        required:true,
        type: Object
      }
    },
    methods: {
      openInner() {
        this.$router.push({ path: 'inner', query: { plan: this.data.id }})
      }
    }
  }
</script>

<style scoped>
.product {
  width:250px;
  border:1px solid red;
  margin-left:30px;
  margin-bottom:50px;
}
.price{
  text-align: center;
}
.product img {
  width:200px;
  cursor:pointer;
  margin:0 auto;
  display:grid;
}
.product-desc .product-name{
  text-align: center;
  line-height: 60px;
}
</style>