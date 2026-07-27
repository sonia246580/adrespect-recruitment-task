<script setup>
import logo from '../../assets/images/logo.svg'
import BaseContainer from '../common/BaseContainer.vue'
import { ChevronDown, Search } from 'lucide-vue-next';
</script>

<template>
    <header class="bg-white">
        <BaseContainer class="flex items-center justify-between py-5">
            <a href="#" aria-label="Strona główna">
                <img
                :src="logo"
                alt="giarddesign"
                class="h-auto w-[115px]"
                />
            </a>
            
            <div class="flex items-center gap-10">
                <nav aria-label="Główna nawigacja">
                    <ul class="flex items-center gap-12">
                        <li>
                            <button
                                type="button"
                                class="flex items-center gap-1 text-[14px] font-normal"
                            >

                                Oferta
                                <ChevronDown :size="14" :stroke-width="1.5" />
                            </button>
                        </li>

                        <li>
                            <a href="#" class="text-[14px] font-normal">
                                O firmie
                            </a>
                        </li>

                        <li>
                            <a href="#" class="text-[14px] font-normal">
                                Realizacje
                            </a>
                        </li>

                        <li>
                            <a href="#" class="text-[14px] font-normal">
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