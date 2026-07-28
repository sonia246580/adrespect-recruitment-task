<script setup>
import BaseContainer from '../components/common/BaseContainer.vue'
import ServiceCard from '../components/common/ServiceCard.vue'

const services = [
    {
        title: 'Projekty',
        description:
            'Zaprojektujemy Twój ogród w nowoczesnym stylu i z najlepszym wykorzystaniem istniejącej przestrzeni.',
        link: 'Dowiedz się więcej',
        icon: 'project',
    },
    {
        title: 'Wizualizacje',
        description:
            'Przedstawimy Ci projekty koncepcyjne w postaci wirtualnego spaceru animowanego w technologii 3D.',
        link: 'Dowiedz się więcej',
        icon: 'eye',
    },
    {
        title: 'Realizacje',
        description:
            'Zrealizujemy Twoje marzenie przy użyciu najnowszych rozwiązań i zaawansowanych technologii.',
        link: 'Zobacz nasze realizacje',
        icon: 'stars',
    },
]
</script>

<template>
    <section class="bg-[#F5F0EC] py-20 md:py-32">
        <BaseContainer>
            <div class="mx-auto w-full max-w-[1262px]">
                <p class="text-xs text-[#1B5B31]">Oferta</p>

                <h2 class="hero-title mt-4 max-w-[700px] text-[36px] leading-[1.15] md:text-[48px] text-[#111111]">
                    Działamy <span class="italic font-medium">kompleksowo</span>
                </h2>

                <p class="mt-8 w-full max-w-[710px] text-[16px] leading-[26px] text-[#111111]">
                    Oferujemy kompletną obsługę inwestycji terenów zielonych. Projektujemy
                    nowoczesne ogrody przydomowe oraz rezydencjonalne. Stworzymy dla Ciebie
                    projekt, zwizualizujemy go i wcielimy w życie, a na każdym etapie
                    posłużymy radą i wieloletnim doświadczeniem.
                </p>

                <div class="mt-12 grid gap-8 justify-between md:mt-20 grid-cols-1 lg:grid-cols-3">
                    <ServiceCard
                        v-for="service in services"
                        :key="service.title"
                        v-bind="service"
                    />
                </div>
            </div>    
        </BaseContainer>
    </section>
</template>