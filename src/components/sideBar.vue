<template>
    <div class="md:hidden mobile-nav">
        <div class="w-10 z-20 px-1 fixed top-5 left-5 md:hidden cursor-pointer" @click="toggleSidebar">
            <span :class="{ 'bar': true, 'open': sidebarOpen }" v-for="(bar, index) in 3" :key="index"></span>
        </div>
        <asidecontent :class="{ 'open': sidebarOpen, 'hidden': !sidebarOpen }"/>
    </div>
    <div class="hidden md:block">
        <asidecontent />
    </div>
</template>
  
<script setup>
import { ref } from 'vue';
import asidecontent from './asideContent.vue'

const sidebarOpen = ref(false);

const toggleSidebar = () => {
    sidebarOpen.value = !sidebarOpen.value;
};
</script>
  
<style scoped>
::-webkit-scrollbar{
     width: .5rem;
     background: #ebebeb;
 }
::-webkit-scrollbar-thumb{
     background: #666;
 }
.bar {
    width: 100%;
    height: 3px;
    background-color: gray;
    display: block;
    margin-bottom: 4px;
    transition: transform 0.2s ease-in-out;
}

.bar.open:nth-child(1) {
    transform: rotate(-45deg) translate(-3px, 6.9px);
}

.bar.open:nth-child(2) {
    opacity: 0;
}

.bar.open:nth-child(3) {
    transform: rotate(45deg) translate(-3px, -6.9px);
}

.open {
    transform: translateX(0);
}

.hidden {
    transform: translateX(-100%);
}
</style>
  