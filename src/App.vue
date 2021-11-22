<template>
  <div id="app" >
    <div id="nav" class="text-center p-10 text-xl bg-green-100 font-serif">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
  </div>
</template>
