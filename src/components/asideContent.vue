<template>
    <aside
        class="h-screen overflow-y-scroll bg-black w-full md:w-[300px] fixed top-0 left-0 transition-transform duration-300 py-10 flex items-center justify-center">
        <div class="flex flex-col items-center justify-center gap-8">
            <div class="w-36 h-36 md:mt-10">
                <img class="w-full h-full rounded-full" src="@/assets/images/adeola.jpg" alt="image of Ajijola Adeola">
            </div>
            <div>
                <h2 class="font-bold font-[Quicksand] text-2xl mb-1 text-center dark:text-white">Ajijola Adeola</h2>
                <p class="fold-medium font-[Lancelot] text-base text-[#2C98F0] text-center dark:text-white">Frontend Developer</p>
            </div>
            <nav class="flex flex-col items-center gap-1">
                <a class="font-[Lancelot] font-light text-xl hover:text-[#2C98F0] duration-300 dark:text-white"
                    v-for="(link, index) in links" :key="index" :href="link.url" :class="{ active: activeLink === index }"
                    @click="scrollToSection(index)">
                    {{ link.text }}
                </a>
            </nav>
            <footer class="mb-10 md:mb-0">
                <p class="font-[Lancelot] text-base font-normal text-center dark:text-white">&copy; 2023 All right Reserved</p>
                <p class="font-[Lancelot] text-base font-normal text-center dark:text-white">Made with ❤ by <span
                        class="text-[#2C98F0]">Adeola</span></p>
            </footer>
        </div>
    </aside>
</template>
<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';

const sidebarOpen = ref(false);

const links = ref([
    { text: 'Home', url: '#Home' },
    { text: 'About', url: '#About' },
    { text: 'Services', url: '#Services' },
    { text: 'Skills', url: '#Skills' },
    { text: 'Education', url: '#Education' },
    { text: 'Experience', url: '#Experience' },
    { text: 'Work', url: '#Work' },
    { text: 'Blog', url: '#Blog' },
    { text: 'Contact', url: '#Contact' },
]);

const activeLink = ref(0);

const scrollToSection = (index) => {
    const sectionId = links.value[index].url.substring(1);
    const sectionElement = document.getElementById(sectionId);
    if (sectionElement) {
        sectionElement.scrollIntoView({ behavior: 'smooth' });
        activeLink.value = index;
        sidebarOpen.value = false;
    }
};

const updateActiveLink = () => {
    const scrollPosition = window.scrollY;

    if (scrollPosition === 0) {
        activeLink.value = 0;
        return;
    }
    for (let i = 0; i < links.value.length; i++) {
        const sectionId = links.value[i].url.substring(1);
        const sectionElement = document.getElementById(sectionId);

        if (sectionElement) {
            const sectionTop = sectionElement.offsetTop;
            const sectionBottom = sectionTop + sectionElement.offsetHeight;

            if (scrollPosition >= sectionTop && scrollPosition < sectionBottom) {
                activeLink.value = i;
                break;
            }
        }
    }
};

onMounted(() => {
    updateActiveLink();
    window.addEventListener('scroll', updateActiveLink);
});

onBeforeUnmount(() => {
    window.removeEventListener('scroll', updateActiveLink);
});
</script>



