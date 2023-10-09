<template>
  <section class="h-screen w-full px-8 lg:px-20 flex items-center" id="Home">
    <transition name="fade" mode="out-in">
      <div :key="currentBlock" class="flex flex-col gap-6">
        <div v-if="currentBlock === 1">
          <h1 class="font--[Quicksand] text-4xl sm:text-5xl font-bold dark:text-white">Hi!</h1>
          <h1 class="font--[Quicksand] text-4xl sm:text-5xl font-bold dark:text-white">
            I'm Adeola
          </h1>
        </div>
        <div v-else>
          <h1 class="font--[Quicksand] text-4xl sm:text-5xl font-bold dark:text-white">I am a</h1>
          <h1 class="font--[Quicksand] text-4xl sm:text-5xl font-bold dark:text-white">
            Frontend Developer
          </h1>
        </div>
        <p class="font-[Lancelot] font-normal text-2xl dark:text-white">
          Crafting Exceptional Web Experiences
        </p>
        <div>
          <a href="/AyodeleResume.pdf" target="_blank" rel="noopener noreferrer" download>
            <button
              class="border border-solid border-gray-500 py-2 px-10 font-[Lancelot] font-400 text-xl dark:text-white"
            >
              Download CV
            </button>
          </a>
        </div>
      </div>
    </transition>
  </section>
</template>
<script setup>
import { ref, watchEffect, onUnmounted } from 'vue'

const currentBlock = ref(1)

const toggleBlock = () => {
  currentBlock.value = currentBlock.value === 1 ? 2 : 1
}

const interval = setInterval(toggleBlock, 10000)

watchEffect(() => {
  onUnmounted(() => {
    clearInterval(interval)
  })
})
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
