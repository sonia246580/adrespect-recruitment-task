<script setup>
import logo from '../../assets/images/logo.svg'
import BaseContainer from '../common/BaseContainer.vue';
import { ChevronDown, Search } from 'lucide-vue-next';
</script>

<template>
    <header class="h-[72px] bg-white">
        <BaseContainer class="flex h-full items-center justify-between">
            <a href="#" aria-label="Strona główna">
                <img
                :src="logo"
                alt="giarddesign"
                class="h-auto w-[114.37px]"
                />
            </a>
            
            <div class="flex items-center gap-10">
                <nav aria-label="Główna nawigacja">
                    <ul class="flex items-center gap-12">
                        <li>
                            <button
                                type="button"
                                class="flex items-center gap-1 text-[14px] font-normal leading-none"
                            >

                                Oferta
                                <ChevronDown :size="14" :stroke-width="1.5" />
                            </button>
                        </li>

                        <li>
                            <a href="#" class="text-[14px] font-normal leading-none">
                                O firmie
                            </a>
                        </li>

                        <li>
                            <a href="#" class="text-[14px] font-normal leading-none">
                                Realizacje
                            </a>
                        </li>

                        <li>
                            <a href="#" class="text-[14px] font-normal leading-none">
                                Kontakt
                            </a>
                        </li>
                    </ul>
                </nav>

                <button
                    type="button"
                    aria-label="Szukaj"
                    class="flex h-6 w-6 items-center justify-center"
                >
                    <Search :size="24" :stroke-width="1.5" />
                </button>
            </div>
        </BaseContainer>
    </header>
</template>