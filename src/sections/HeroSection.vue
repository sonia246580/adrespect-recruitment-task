<script setup>
import { ArrowDown, ArrowLeft, ArrowRight } from 'lucide-vue-next'
import BaseButton from '../components/common/BaseButton.vue'
import heroImage from '../assets/images/hero.jpg'
</script>

<template>
    <section class="grid min-h-[808px] grid-cols-2 bg-[#DCC1AB]">
        <div class="flex items-center">
            <div class="w-full max-w-[630px] pl-16 pr-12">
                <h1 class="hero-title max-w-[520px] text-[64px] font-normal leading-[1.16] tracking-[-0.02em] text-[#111111]">
                    Nowoczesna aranżacja Twojego ogrodu
                </h1>

                <p class="mt-12 max-w-[490px] text-base leading-[1.65] text-black">
                    Marka GiardDesign to wieloletnie doświadczenie i wysoka 
                    estetyka realizacji. Oferujemy kompleksowy zakres usług
                    z indywidualnym podejściem do każdego projektu.
                </p>

                <div class="mt-16 flex items-center gap-10">
                    <BaseButton>
                        Skontaktuj się z nami
                    </BaseButton>

                    <BaseButton variant="outline" class="gap-2">
                        Zobacz nasze realizacje
                        <ArrowDown :size="20" :stroke-width="1.5" />
                    </BaseButton>
                </div>
            </div>
        </div>

        <div class="relative min-h-[808px] overflow-hidden">
           <img
           :src="heroImage"
           alt="Nowoczesna aranżacja Twojego ogrodu"
           class="h-full w-full object-cover"
           />

           <div class="absolute bottom-0 right-0 flex bg-[#F5F0EC]">
            <button
                type="button"
                aria-label="Poprzedni slajd"
                class="flex h-[104px] w-[104px] items-center justify-center"
            >
                <ArrowLeft :size="34" :stroke-width="1.5" />
            </button>

            <button 
                type="button"
                aria-label="Następny slajd"
                class="flex h-[104px] w-[104px] items-center justify-center"
            >
                <ArrowRight :size="34" :stroke-width="1.5" />
            </button>
           </div>
        </div>
    </section>
</template>