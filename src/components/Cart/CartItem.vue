<template>
            <div class="product">
              <div class="image">
                <img :src="data.url" alt="" @click="openInner">
              </div>
            <div class="product-data">
              <h1>{{ data.title }}</h1>
            <p class="desc">{{ data.desc }}</p>
            <p class="amount">{{ data.amount }} X</p>
            <p>{{ data.price }} $</p>
            <button class="delete-button" @click="sendId">Delete</button>
            </div>
            </div>
            <hr>
      </template>
    
    <script>
    export default {
      props: {
        data: {
          required:true,
          type:Object
        }
      },
        data() {
            return {}
        },
        methods: {
      openInner() {
        this.$router.push({ path: 'inner', query: { plan: this.data.id }})
      },
      sendId() {
        this.$emit('getId', this.data.id)
      }
    }
    }
    </script>
      
      <style scoped>
      .product {
        display:flex;
        margin-top:50px;
        flex-wrap:wrap;
      }
      .image img {
      width:150px;
      margin-left:60px;
      cursor:pointer;
    }
    .product-data {
      width:500px;
      margin-left:50px;
      margin-bottom:20px;

    }
    .product-data .amount {
      line-height:30px;
    }
    .product-data .delete-button {
      padding: 5px 5px;
      margin-top:10px;
      border:1px solid black;
    }
    button {
      cursor:pointer;
    }
      </style>