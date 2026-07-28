<script setup>
import { ArrowRight } from 'lucide-vue-next'
import aboutImage from '../assets/images/about.jpg'
</script>

<template>
    <section class="relative grid min-h-[860px] grid-cols-1 lg:grid-cols-2 lg:bg-[#1B5B31]">
		<div class="absolute top-0 left-0 -z-10 w-full h-full hero-linear-gradient lg:hidden"></div>
		<div class="absolute inset-0 bg-[url('./assets/images/about.jpg')] bg-position-center bg-cover bg-no-repeat -z-20 lg:z-0 lg:left-1/2 lg:w-1/2"></div>

        <div class="text-[#F5F0EC] mt-auto pb-16 sm:mt-0 sm:pb-0">
            <div class="flex h-full w-full lg:max-w-[596px] flex-col justify-center px-[clamp(24px,5vw,89px)] text-[#F5F0EC]">
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
                    class="mt-14 inline-flex h-[50px] w-[194px] items-center justify-center gap-2 rounded-[200px] border border-[#F5F0EC]"
                >
                    Poznaj nas bliżej
                    <ArrowRight :size="20" :stroke-width="1.5" />
                </a>
            </div>
        </div>
    </section>
</template>