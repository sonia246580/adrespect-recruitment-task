<script setup>
import { computed, nextTick, onBeforeUnmount, onMounted, ref, watch } from 'vue'
import { ArrowDown } from 'lucide-vue-next'
import Masonry from 'masonry-layout'
import imagesLoaded from 'imagesloaded'
import VueEasyLightbox from 'vue-easy-lightbox'

import project1 from '../assets/images/projects/project-1.jpg'
import project2 from '../assets/images/projects/project-2.jpg'
import project3 from '../assets/images/projects/project-3.jpg'
import project4 from '../assets/images/projects/project-4.jpg'
import project5 from '../assets/images/projects/project-5.jpg'
import project6 from '../assets/images/projects/project-6.jpg'
import project7 from '../assets/images/projects/project-7.jpg'
import project8 from '../assets/images/projects/project-8.jpg'
import project9 from '../assets/images/projects/project-9.jpg'

const MOBILE_BREAKPOINT = 768
const MOBILE_INITIAL_COUNT = 4
const DESKTOP_INITIAL_COUNT = 6
const PROJECTS_PER_LOAD = 3

const projects = [
    { src: project1, alt: 'Realizacja ogrodu 1' },
    { src: project2, alt: 'Realizacja ogrodu 2' },
    { src: project3, alt: 'Realizacja ogrodu 3' },
    { src: project4, alt: 'Realizacja ogrodu 4' },
    { src: project5, alt: 'Realizacja ogrodu 5' },
    { src: project6, alt: 'Realizacja ogrodu 6' },
    { src: project7, alt: 'Realizacja ogrodu 7' },
    { src: project8, alt: 'Realizacja ogrodu 8' },
    { src: project9, alt: 'Realizacja ogrodu 9' },
]

const masonryGrid = ref(null)
const visibleCount = ref(MOBILE_INITIAL_COUNT)
const lightboxVisible = ref(false)
const lightboxIndex = ref(0)
const isMobile = ref(true)

let masonryInstance = null
let imagesLoadedInstance = null

const visibleProjects = computed(() => 
    projects.slice(0, visibleCount.value)
)

const lightboxImages = computed(() => 
projects.map((project) => project.src)
)

const hasMoreProjects = computed(() => 
visibleCount.value < projects.length)



const destroyMasonry = () => {
    imagesLoadedInstance?.off('progress')
    imagesLoadedInstance?.off('always')
    masonryInstance?.destroy()

    imagesLoadedInstance = null
    masonryInstance = null

    if (!masonryGrid.value) {
        return
    }

    const items = masonryGrid.value.querySelectorAll('.project-item')

    items.forEach((item) => {
        item.style.position = ''
        item.style.left = ''
        item.style.top = ''
        item.style.transform = ''
    })

    masonryGrid.value.style.height = ''
}

const initializeMasonry = async () => {
    await nextTick()

    if (!masonryGrid.value) return

    destroyMasonry()

    masonryInstance = new Masonry(masonryGrid.value, {
        itemSelector: '.project-item',
        columnWidth: '.project-sizer',
        gutter: 24,
        percentPosition: true,
        transitionDuration: '0.35s',
    })

    imagesLoadedInstance = imagesLoaded(masonryGrid.value)

    imagesLoadedInstance.on('progress', () => {
        masonryInstance?.layout()
    })

    imagesLoadedInstance.on('always', () => {
        masonryInstance?.layout()
    })
}

const updateViewport = () => {
    const wasMobile = isMobile.value

    isMobile.value = window.innerWidth < MOBILE_BREAKPOINT

    if (isMobile.value && !wasMobile) {
        visibleCount.value = Math.max(
            visibleCount.value,
            MOBILE_INITIAL_COUNT,
        )
    }

    if (!isMobile.value && wasMobile) {
        visibleCount.value = Math.max(
            visibleCount.value,
            DESKTOP_INITIAL_COUNT,
        )
    }

    initializeMasonry()
}

const showMoreProjects = () => {
    visibleCount.value = Math.min(
        visibleCount.value + PROJECTS_PER_LOAD, 
        projects.length)
}

const openLightbox = (index) => {
    lightboxIndex.value = index
    lightboxVisible.value = true
}

watch(visibleCount, initializeMasonry)

onMounted(() => {
    isMobile.value = window.innerWidth < MOBILE_BREAKPOINT

    visibleCount.value = isMobile.value
        ? MOBILE_INITIAL_COUNT
        : DESKTOP_INITIAL_COUNT

    window.addEventListener('resize', updateViewport)

    initializeMasonry()
})

onBeforeUnmount(() => {
    window.removeEventListener('resize', updateViewport)
    destroyMasonry()
})

</script>

<template>
    <section
        id="realizacje"
        class="relative overflow-hidden bg-[#DCC1AB] py-12 md:py-20 lg:py-28"
    >
        <div class="mx-auto w-full max-w-[1440px] px-4 sm:px-6 lg:px-10">
            <div class="mx-auto mb-8 max-w-[1260px] md:mb-12 lg:mb-16">
                <p class="text-xs text-[#1B5B31]">
                    Realizacje
                </p>

                <h2
                    class="hero-title mt-3 text-[32px] leading-[1.1] text-[#111111] md:mt-4 md:text-[44px] lg:text-[48px]"
                >
                    Nasze <span class="italic">projekty</span>
                </h2>
            </div>
        </div>

            <div
                ref="masonryGrid"
                class="projects-grid relative mx-auto max-w-[1260px]"
            >
                <div
                    class="project-sizer hidden md:block md:w-[calc((100%_-_24px)/2)] lg:w-[calc((100%_-_48px)/3)]"
                    aria-hidden="true"
                />

                <button
                    v-for="(project, index) in visibleProjects"
                    :key="project.src"
                    type="button"
                    class="project-item mb-4 block cursor-zoom-in appearance-none overflow-hidden border-0 bg-transparent p-0 text-left md:mb-6 md:w-[calc((100%_-_24px)/2)] lg:w-[calc((100%_-_48px)/3)]"
                    :aria-label="`Otwórz zdjęcie: ${project.alt}`"
                    @click="openLightbox(index)"
                >
                    <img
                        :src="project.src"
                        :alt="project.alt"
                        class="block h-auto w-full object-cover transition-transform duration-500 ease-out hover:scale-105"
                        loading="lazy"
                        decoding="async"
                    />
                </button>
            </div>

            <div
                v-if="hasMoreProjects"
                class="mt-8 flex justify-center"
            >
        
                <button
                    type="button"
                    class="inline-flex items-center gap-2 rounded-full border border-[#111111] bg-[#DCC1AB] px-6 py-3 text-sm text-[#111111] transition hover:bg-[#111111] hover:text-white"
                    @click="showMoreProjects"
                >
                    Rozwiń
                    <ArrowDown :size="18" :stroke-width="1.5" />
                </button>
            </div>

        <VueEasyLightbox
            :visible="lightboxVisible"
            :imgs="lightboxImages"
            :index="lightboxIndex"
            @hide="lightboxVisible = false"
        />
    </section>
</template>

<style scoped>
@media (max-width: 767px) {
    .projects-grid {
        display: flex;
        flex-direction: column;
    }

    .project-item {
        position: relative !important;
        top: auto !important;
        left: auto !important;
        width: 84%;
        transform: none !important;
    }

    .project-item:nth-of-type(odd) {
        align-self: flex-start;
    }

    .project-item:nth-of-type(even) {
        align-self: flex-end;
    }

    .project-item:nth-of-type(3n) {
        width: 92%;
    }

    .project-item:nth-of-type(4n) {
        width: 78%;
    }
}
</style>
