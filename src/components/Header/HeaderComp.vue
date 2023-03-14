<template>
    <div class="bg-green">
        <router-link to="/"><p class="logo">Ecommerce</p></router-link>
        <div class="reg-log">
       <router-link to="/cart"><p>Cart <span>{{ getProductLength }}</span></p></router-link>
        </div>
    </div>
</template>

<script>
import store from '../../store/index'
export default {
    computed: {
        getProductLength() {
            return store.getters.getProducts.length
        }
    }
}
</script>

<style scoped>
* {
    text-decoration: none;
}
.logo {
    color:white;
}
.bg-green {
    background-color: green;
    padding:20px 16px;
    display:flex;
    justify-content: center;
    justify-content: space-between;
    color:white;
}
.reg-log p {
    color:white;
}
.reg-log {
    display:flex;
}
.reg-log p {
    margin-right:50px;
}
</style>