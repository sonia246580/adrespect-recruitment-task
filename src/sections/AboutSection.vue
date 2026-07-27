<script setup>
import { ArrowRight } from 'lucide-vue-next'
import aboutImage from '../assets/images/about.jpg'
</script>

<template>
    <section class="grid min-h-[720px] grid-cols-2 bg-[#1B5B31]">
        <div class="min-h-[720px] overflow-hidden">
            <img
                :src="aboutImage"
                alt="Nowoczesny ogród przy domu"
                class="h-full w-full object-cover"
            />
        </div>

        <div class="flex items-center text-[#F5F0EC]">
            <div class="w-full max-w-[630px] px-20">
                <p class="text-xs">
                    O firmie
                </p>

                <h2
                    class="hero-title mt-7 max-w-[430px] text-[48px] font-normal leading-[1.15]"
                >
                    Tworzymy<br />
                    z <span class="italic">pasją</span>
                </h2>

                <p class="mt-12 max-w-[520px] text-[16px] leading-[28px]">
                    Każdy projekt to nowe wyzwanie. Dlatego nasz zespół tworzą
                    wykwalifikowani projektanci oraz architekci, których zadaniem jest
                    rozpoznanie i realizacja potrzeb każdego Klienta. Nasza specjalizacja
                    to przestrzenie nowoczesne, które charakteryzuje minimalizm, geometria
                    i elegancka prostota. Tworzymy ogrody małoobsługowe, dostosowane do
                    współczesnego trybu życia.
                </p>

                <a
                    href="#"
                    class="mt-16 inline-flex items-center gap-3 rounded-full border border-[#F5F0EC] px-7 py-4 text-[16px] transition hover:bg-[#F5F0EC] hover:text-[#1B5B31]"
                >
                    Poznaj nas bliżej
                    <ArrowRight :size="20" :stroke-width="1.5" />
                </a>
            </div>
        </div>
    </section>
</template>