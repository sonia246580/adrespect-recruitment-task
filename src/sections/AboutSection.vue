<script setup>
import { ArrowRight } from 'lucide-vue-next'
import aboutImage from '../assets/images/about.jpg'
</script>

<template>
    <section class="grid min-h-[860px] grid-cols-2 bg-[#1B5B31]">
        <div class="min-h-[860px] overflow-hidden">
            <img
                :src="aboutImage"
                alt="Nowoczesny ogród przy domu"
                class="h-full w-full object-cover"
            />
        </div>

        <div class="text-[#F5F0EC]">
            <div class="flex w-full max-w-[596px] flex-col pl-[96px] pt-[135px] text-[#F5F0EC]">
                <p class="text-[12px] leading-[18px] text-[#F5F0EC]">
                    O firmie
                </p>

                <h2
                    class="hero-title mt-6 max-w-[430px] text-[48px] font-normal leading-[1.08] tracking-[-0.02em]"
                >
                    Tworzymy<br />
                    z <span class="italic">pasją</span>
                </h2>

                <p class="mt-10 max-w-[500px] text-[16px] leading-[28px]">
                    Każdy projekt to nowe wyzwanie. Dlatego nasz zespół tworzą
                    wykwalifikowani projektanci oraz architekci, których zadaniem jest
                    rozpoznanie i realizacja potrzeb każdego Klienta. Nasza specjalizacja
                    to przestrzenie nowoczesne, które charakteryzuje minimalizm, geometria
                    i elegancka prostota. Tworzymy ogrody małoobsługowe, dostosowane do
                    współczesnego trybu życia.
                </p>

                <a
                    href="#"
                    class="mt-14 inline-flex items-center gap-3 rounded-full border border-[#F5F0EC] px-6 py-[14px] text-[16px] transition-all duration-300 hover:bg-[#F5F0EC] hover:text-[#1B5B31]"
                >
                    Poznaj nas bliżej
                    <ArrowRight :size="20" :stroke-width="1.5" />
                </a>
            </div>
        </div>
    </section>
</template>