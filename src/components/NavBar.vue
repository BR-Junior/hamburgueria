<template>
    <div id="nav">
    <router-link to="/" id="logo_url">
        <img :src="logo" :alt="alt" id="logo">
    </router-link>
    <router-link to="/">Home</router-link> 
    <router-link to="/pedidos">Pedidos</router-link>
    </div>
</template>
<script setup lang="ts">
const props = defineProps({
    logo: {
        type: String,
        default: ''
    },
    alt: {
        type: String,
        default: ''
    } 
})



</script>

<style scoped>
#nav{
    background-color: #222;
    border-bottom: 4px solid #111;
    padding: 15px 15px;
    display: flex;
    justify-content: flex-end;
    align-items: center;
}

#nav #logo_url{
    margin: auto;
    margin-left: 0;
}

#logo{
    width: 40px;
    height: 40px;
}

#nav a{
    color: #fcba03;
    text-decoration: none;
    margin: 12px;
    transform: .5s;
}

#nav a:hover{
    color: #fff;
}

</style>