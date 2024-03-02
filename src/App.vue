<template>
  <a-layout :style="{ background: '#fff' }">
    <CarouselBanner />
    <Content />
  </a-layout>
</template>

<script setup>
import Content from "./components/Content.vue";
import CarouselBanner from "./components/CarouselBanner.vue";
</script>

<style scoped>
#components-layout-demo-fixed .logo {
  width: 120px;
  height: 31px;
  background: rgba(255, 255, 255, 0.2);
  margin: 16px 24px 16px 0;
  float: left;
}
</style>
