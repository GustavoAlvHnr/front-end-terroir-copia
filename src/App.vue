<script setup>
import { RouterLink, RouterView } from 'vue-router'
import AppHeader from './components/layout/appHeader.vue'

</script>

<template>
  <appHeader show-menu show-cart />
  <RouterView />
</template>

<style scoped>

</style>
