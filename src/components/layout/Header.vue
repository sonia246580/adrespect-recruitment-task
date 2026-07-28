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

            <div class="flex lg:hidden items-center gap-10">
                <Search :size="24" :stroke-width="1.5" />
                <Menu :size="24" :stroke-width="1.5" />
            </div>
            
            <div class="hidden lg:flex items-center gap-10">
                <nav aria-label="Główna nawigacja" class="text-[14px] font-normal">
                    <ul class="flex items-center gap-12">
                        <li>
                            <button class="flex items-center-1">
                                Oferta
                                <ChevronDown :size="14" :stroke-width="1.5" />
                            </button>
                        </li>

                        <li>
                            <a href="#">O firmie</a>
                        </li>

                        <li>
                            <a href="#">Realizacje</a>
                        </li>

                        <li>
                            <a href="#">Kontakt</a>
                        </li>
                    </ul>
                </nav>
                <Search :size="24" :stroke-width="1.5" /> 
            </div>
        </BaseContainer>
    </header>
</template>