<template>
  <Header />
  <main class="container">
    <router-view></router-view>
  </main>
</template>

<script setup>
import Header from "@/components/layout/Header.vue"
</script>