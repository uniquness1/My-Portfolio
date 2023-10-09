<template>
  <main class="flex justify-between max-w-8xl w-full mx-auto h-screen">
    <div>
      <SideBar />
    </div>
    <Content class="md:ml-[18rem]"/>
  </main>
</template>

<script setup>
import SideBar from '@/components/sideBar.vue'
import Content from '@/components/contentSide.vue'
</script>
<style scoped></style>