<script setup>
import { computed } from 'vue'

const props = defineProps({
    variant: {
        type: String,
        default: 'primary',
        validator: (value) => ['primary', 'secondary'].includes(value),
    },

    outline: {
        type: Boolean,
        default: false,
    },

    type: {
        type: String,
        default: 'button',
    },
})

const variantClasses = computed(() => {
    const variants = {
        primary: {
            solid: 'border border-[#1B5B31] bg-[#1B5B31] text-white hover:bg-[#144625] hover:border-[#144625]',
            outline: 'border border-[#1B5B31] bg-transparent text-[#1B5B31] hover:bg-[#1B5B31] hover:text-white',
        },
        secondary: {
            solid: 'border border-white bg-white text-[#1B5B31] hover:bg-[#F0F5F1] hover:border-[#F0F5F1]',
            outline: 'border border-white bg-transparent text-white hover:bg-white hover:text-[#1B5B31]',
        },
    }

     return variants[props.variant][props.outline ? 'outline' : 'solid']
})

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