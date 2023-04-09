<template>
    <div class="not-found">
        <h1>404: Page Not Found</h1>
        <h1> <router-link to="/"><span class="continue">Continue shopping</span></router-link></h1>
    </div>
</template>

<style scoped>
.not-found {
    text-align:center;
    align-items:center;
    margin-top:10%;
}
* {
    text-decoration: none;
}
.continue {
    color:black;
    text-decoration: underline;
}
</style>