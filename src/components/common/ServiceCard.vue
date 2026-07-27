<script setup>
import { ArrowRight, Pencil, Eye, Sparkles } from 'lucide-vue-next'
import { computed } from 'vue'

const props = defineProps({
    title: String,
    description: String,
    link: String,
    icon: String,
})

const iconComponent = computed(() => {
    switch (props.icon) {
        case 'project':
            return Pencil
        case 'eye':
            return Eye
        case 'stars':
            return Sparkles
        default:
            return Pencil
  }
})
</script>

<template>
    <article
        class="flex h-full flex-col rounded-[28px] bg-white p-12 transition-all duration-300 hover:-translate-y-2 hover:shadow-xl"
    >
        <component :is="iconComponent" :size="40" class="text-black" />

        <h3 class="hero-title mt-8 text-[28px] leading-[1.2] text-[#111111]">
            {{ title }}
        </h3>

        <p class="mt-6 flex-1 text-[16px] leading-[26px] text-[#111111]">
            {{ description }}
        </p>

        <a
            href="#"
            class="mt-10 inline-flex items-center gap-2 self-start border-b border-[#1B5B31] pb-1 text-[#1B5B31] transition hover:gap-3"
        >
            {{ link }}
            <ArrowRight :size="20" />
        </a>
    </article>
</template>