<template>
        <div class="product">
            <div class="image">
                <img :src="currentData[0].url" alt="">
            </div>
        <div class="product-data">
            <h1 class="title">{{ currentData[0].title }}</h1>
        <p class="desc">{{ currentData[0].desc }}</p>
        <p class="balance">{{ balance }} $</p>
            <div class="buttons">
            <button class="minus" @click="minus" :disabled="disableBut">-</button>
            <p class="counter">{{ counter }}</p>
            <button class="plus" @click="plus" :disabled="disableBut">+</button>
            </div>
            <div class="add-cart-button">
                <button @click="addItem" :disabled="disableBut">Add To Cart</button>
            </div>
        </div>
        </div>
  </template>

<script>
import prData from '../../Products.json'
import store from '../../store/index'
export default {
    data() {
        return {
            currentData: prData,
            counter: 1,
            balance: 0,
            addedItem:[],
            disableBut: false,
        }
    },
    methods: {
        minus() {
            if(this.counter <= 1) {
                return
            }
            this.counter--
            this.dencrementBalance()
        },
        plus() {
            this.counter++,
           this.incrementBalance()
        },
        incrementBalance() {
           this.balance += this.currentData[0].price
        },
        dencrementBalance() {
            this.balance -= this.currentData[0].price
        },
        disableButton() {
            store.getters.getProducts.forEach((element) => {
                if(element.id == this.currentData[0].id) {
                    this.disableBut = true
                }
            })
        },
        addItem() {
            this.addedItem = {
            id: this.currentData[0].id,
            title: this.currentData[0].title,
            url: this.currentData[0].url,
            desc:  this.currentData[0].desc,
            price: this.balance,
            amount: this.counter,
            }
            store.commit('setProduct', this.addedItem)
            localStorage.setItem('cartItems', JSON.stringify(store.state.cartProducts))
            this.disableButton()
        }
    },
    mounted() {
        this.currentData = prData.filter(el => el.id === parseInt(this.$route.query.plan))
        this.balance = this.currentData[0].price
        this.disableButton()
    },
}
</script>
  
  <style scoped>
.product {
    display:flex;
    justify-content:center;
    margin-top:100px;
}
.product .image img {
    width:200px;
}
.product-data {
    width:500px;
    margin-left:50px;
}
.product-data .balance {
    line-height:50px;
}
.buttons {
    display:flex;
    margin-bottom:30px;
}
.buttons .minus{
    margin-right:10px;
}
.buttons .plus {
    margin-left:10px;
}
.buttons button {
    padding:2px 5px;
    cursor:pointer;
    border:1px solid black;
}
.add-cart-button button{
    padding:10px 15px;
    border-radius:15px;
    border:1px solid black;
    background-color:greenyellow;
    cursor:pointer;
}
  </style>