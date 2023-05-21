<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="container">
      <nav>
        <RouterLink class="menu-link" to="/">Home</RouterLink>
        <RouterLink class="menu-link" to="/about">About</RouterLink>
        <RouterLink class="menu-link" to="/note">Note</RouterLink>

      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
.container{
  background-color: rgb(245, 153, 40);
  height: 65px;
  width: 100%;
  align-content: center;
  justify-content: center;
}
nav{
  padding: 17px 20px;
 
  
}
nav .menu-link{
  color: white;
  padding: 17px 20px;
  text-decoration: none;
  font-family: sans-serif;
  font-size: 20px;
}
</style>
