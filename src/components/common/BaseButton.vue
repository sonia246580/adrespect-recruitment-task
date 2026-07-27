<script setup>
import { computed } from 'vue'

const props = defineProps({
    variant: {
        type: String,
        default: 'primary',
        validator: (value) => ['primary', 'outline'].includes(value),
    },

    type: {
        type: String,
        default: 'button',
    },
})

const variantClasses = computed(() =>
    props.variant === 'outline'
    ? 'border border-[#1B5B31] bg-transparent text-[#1b5b31] hover:bg-[#1B5B31] hover:text-white'
    : 'border border-[#1B5B31] bg-[#1B5B31] text-white hover:bg-[#144625] hover:border-[#144625]'
)
</script>

<template>
    <button
    :type="type"
    :class="[
        'inline-flex items-center justify-center rounder-full px-6 py-3 text-base font-normal transition-colors duration-300',
        variantClasses,
    ]"
    style="border-radius: 9999px;"
    >
        <slot />
    </button>
</template>