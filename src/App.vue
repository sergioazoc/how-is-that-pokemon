<template>
  <div id="nav" class="d-none">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
  <div class="container">
    <router-view/>
  </div>
</template>

<style lang="scss">
#app{
  height: 100vh;
  width: 100vw;
  background-color: #ea332c;
}
</style>
