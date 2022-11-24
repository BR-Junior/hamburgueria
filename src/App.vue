<template>
  <NavBar :logo="logo_src" :alt="app_name"/>  
  <router-view/>
  <Footer />
</template>

<script setup lang="ts">
import NavBar from './components/NavBar.vue'
import Footer from './components/Footer.vue'

const logo_src = "/img/logo.png"
const app_name = 'Make your burger'

</script>

<style>
*{
  font-family: Helvetica;
  padding: 0px;
  margin: 0px;
  box-sizing: border-box;
}

.main-container{
  margin: 50px;
  min-height: 360px;
}

h1{
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}

</style>
