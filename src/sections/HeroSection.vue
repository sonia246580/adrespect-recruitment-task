<script setup>
import { ArrowDown, ArrowLeft, ArrowRight } from 'lucide-vue-next'
import BaseButton from '../components/common/BaseButton.vue'
import heroImage from '../assets/images/hero.jpg'
</script>

<template>
    <section
        class="relative grid h-[calc(100vh-64px)] overflow-hidden bg-[#DCC1AB]"
        style="grid-template-columns: 52.22% 47.78%;"
    >
        <div class="flex items-center">
            <div class="w-full pl-[clamp(24px,5vw,89px)]">
                <div class="w-full max-w-[599px] pr-[48px]">
                    <h1 class="hero-title w-full text-[64px] font-medium leading-[70px] text-[#111111]">
                        <span class="block">Nowoczesna</span>
                        <span class="block">aranżacja</span>
                        <span class="block">Twojego ogrodu</span>
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
        </div>

        <div class="relative h-full overflow-hidden">
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