<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div>
    <img src="./assets/add-friend.png" class="logo"/>
  </div>
  <HelloWorld msg="Nuevo usuario" />
</template>

<style scoped>
.logo {
  height: 6em;
  will-change: filter;
  transition: filter 300ms;
  filter: drop-shadow(0 0 2em #646cffaa);
}
</style>
