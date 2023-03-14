<template>
        <div class="fullbalance">
            <h1>Full Balance</h1>
        <h1>{{ getFullBalance }} GEL</h1>
        </div>
    <p class="fullbalance" v-show="getData.length === 0">Cart is Empty
        <router-link to="/"><span class="continue">Continue shopping</span></router-link>
    </p>
    <CartItem v-for="(item, index) in getData" :key="index" :data="item" @getId="deleteItem" />
</template>

<script>
import store from '../store/index'
import CartItem from '../components/Cart/CartItem.vue'
    export default {
        data() {
            return {
                fullBalance: 0
            }
        },
        components: {
            CartItem
        },
        computed: { 
            getData() {
                return store.getters.getProducts
            },
            getFullBalance() {
                let balance = 0
                this.getData.forEach(item =>{
                    balance += item.price
                })
                return balance
            }
        },
        methods: {
            deleteItem(id) {
                store.commit('removeProduct', id)
                localStorage.setItem('cartItems', JSON.stringify(store.state.cartProducts))
            }
        }
    }
</script>

<style scoped>
.fullbalance {
    width:250px;
    margin: 0 auto;
}
</style>