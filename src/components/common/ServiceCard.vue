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
        class="flex w-full lg:max-w-[378px] lg:min-h-[370px] flex-col rounded-[28px] bg-white p-8 transition-all duration-300 hover:-translate-y-2 hover:shadow-xl md:min-h-[370px] md:p-12"
    >
        <component :is="iconComponent" :size="32" class="ml-1 text-black" />

        <h3 class="hero-title mt-8 text-[24px] leading-[1.2] md:text-[28px] text-[#111111]">
            {{ title }}
        </h3>

        <p class="mt-6 flex-1 text-[15px] leading-[24px] md:text-[16px] md:leading-[26px] text-[#111111]">
            {{ description }}
        </p>

        <a
            href="#"
            class="mt-8 inline-flex items-center gap-2 self-start border-b border-[#1B5B31] pb-1 text-[15px] text-[#1B5B31] transition-all duration-300 hover:gap-3 md:mt-10 md:text-[16px]"
        >
            {{ link }}
            <ArrowRight :size="20" />
        </a>
    </article>
</template>