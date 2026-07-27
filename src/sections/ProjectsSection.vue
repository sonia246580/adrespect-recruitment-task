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
const visibleCount = ref(6)
const lightboxVisible = ref(false)
const lightboxIndex = ref(0)

let masonryInstance = null
let imagesLoadedInstance = null

const visibleProjects = computed(() => projects.slice(0, visibleCount.value))
const lightboxImages = computed(() => projects.map((project) => project.src))
const hasMoreProjects = computed(() => visibleCount.value < projects.length)

const initializeMasonry = async () => {
    await nextTick()

    if (!masonryGrid.value) return

    masonryInstance?.destroy()

    masonryInstance = new Masonry(masonryGrid.value, {
        itemSelector: '.project-item',
        columnWidth: '.project-sizer',
        gutter: 24,
        percentPosition: true,
    })

    imagesLoadedInstance = imagesLoaded(masonryGrid.value)

    imagesLoadedInstance.on('progress', () => {
        masonryInstance?.layout()
    })

    imagesLoadedInstance.on('always', () => {
        masonryInstance?.layout()
    })
}

const showMoreProjects = () => {
    visibleCount.value = Math.min(visibleCount.value + 3, projects.length)
}

const openLightbox = (index) => {
    lightboxIndex.value = index
    lightboxVisible.value = true
}

watch(visibleCount, initializeMasonry)

onMounted(initializeMasonry)

onBeforeUnmount(() => {
    imagesLoadedInstance?.off('progress')
    imagesLoadedInstance?.off('always')
    masonryInstance?.destroy()
})
</script>

<template>
    <section id="realizacje" class="relative bg-[#DCC1AB] py-28">
        <div class="mx-auto w-full max-w-[1440px] px-6 lg:px-10">
            <div class="mx-auto mb-16 max-w-[1260px]">
                <p class="text-xs text-[#1B5B31]">
                    Realizacje
                </p>

                <h2 class="hero-title mt-4 text-[48px] leading-[1.15] text-[#111111]">
                    Nasze <span class="italic">projekty</span>
                </h2>
            </div>

            <div ref="masonryGrid" class="relative">
                <div class="project-sizer w-[calc((100%-48px)/3)]"></div>

                <button
                    v-for="(project, index) in visibleProjects"
                    :key="project.src"
                    type="button"
                    class="project-item mb-6 block w-[calc((100%-48px)/3)] cursor-zoom-in overflow-hidden"
                    :aria-label="`Otwórz zdjęcie: ${project.alt}`"
                    @click="openLightbox(index)"
                >   
                    <img
                        :src="project.src"
                        :alt="project.alt"
                        class="block h-auto w-full object-cover transition duration-500 hover:scale-105"
                    />
                </button>
            </div>

            <div
                v-if="hasMoreProjects"
                class="pointer-events-none absolute inset-x-0 bottom-0 flex h-[280px] items-end justify-center bg-gradient-to-t from-[#DCC1AB] via-[#DCC1AB]/85 to-transparent pb-12"
            >
                <button
                    type="button"
                    class="pointer-events-auto inline-flex items-center gap-2 rounded-full border border-[#111111] px-6 py-3 text-sm text-[#111111] transition hover:bg-[#111111] hover:text-white"
                    @click="showMoreProjects"
                >
                    Rozwiń
                    <ArrowDown :size="18" :stroke-width="1.5" />
                </button>
            </div>
        </div>

        <VueEasyLightbox
            :visible="lightboxVisible"
            :imgs="lightboxImages"
            :index="lightboxIndex"
            @hide="lightboxVisible = false"
        />
    </section>
</template>