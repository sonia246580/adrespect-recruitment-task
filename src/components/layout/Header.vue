<script setup>
import { ref, watch, onWatcherCleanup } from 'vue'
import logo from '../../assets/images/logo.svg'
import BaseContainer from '../common/BaseContainer.vue';
import { ChevronDown, Menu, X, Search } from 'lucide-vue-next';
import Drawer from '../common/Drawer.vue'

const menuOpen = ref(false);
const offerOpen = ref(false);
const offerPopoverOpen = ref(false);
const offerRef = ref(null);

 watch(offerPopoverOpen, (isOpen) => {
    if (!isOpen) return

     const onPointerDown = (e) => {
        if (!offerRef.value?.contains(e.target)) offerPopoverOpen.value = false
    }
    const onKeydown = (e) => {
        if (e.key === 'Escape') offerPopoverOpen.value = false
    }

     document.addEventListener('pointerdown', onPointerDown)
    document.addEventListener('keydown', onKeydown)

     onWatcherCleanup(() => {
        document.removeEventListener('pointerdown', onPointerDown)
        document.removeEventListener('keydown', onKeydown)
    })
})

</script>

<template>
    <header class="h-[72px] bg-white">
        <BaseContainer class="flex h-full items-center justify-between">
            <a href="#" aria-label="Strona główna">
                <img
                :src="logo"
                alt="giarddesign"
                class="h-auto w-[128px]"
                />
            </a>

            <div class="flex sm:hidden items-center gap-10">
				<Search :size="24" :stroke-width="1.5" />
				<Menu :size="24" :stroke-width="1.5" @click="menuOpen = true"/>
			</div>
            
            <div class="hidden sm:flex items-center gap-10">
                <nav aria-label="Główna nawigacja" class="text-[14px] font-normal">
                    <ul class="flex items-center gap-12">
                        <li ref="offerRef" class="relative">
							<button
								type="button"
								class="flex gap-2"
								:aria-expanded="offerPopoverOpen"
								@click="offerPopoverOpen = !offerPopoverOpen"
							>
								Oferta
								<ChevronDown
									:size="20"
									:stroke-width="1.5"
									class="transition-transform duration-200 ease-out"
									:class="{ 'rotate-180': offerPopoverOpen }"
								/>
							</button>
                            <Transition
								enter-active-class="transition duration-150 ease-out"
								enter-from-class="opacity-0 -translate-y-1"
								leave-active-class="transition duration-100 ease-in"
								leave-to-class="opacity-0 -translate-y-1"
							>
								<ul
									v-show="offerPopoverOpen"
									class="absolute left-1/2 top-full z-30 mt-2 flex min-w-48 -translate-x-1/2 flex-col gap-4 bg-white p-8 shadow"
								>
									<li><a href="#services" @click="offerPopoverOpen = false">Projekty</a></li>
									<li><a href="#services" @click="offerPopoverOpen = false">Wizualizacje</a></li>
									<li><a href="#services" @click="offerPopoverOpen = false">Realizacje</a></li>
								</ul>
							</Transition>
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

    <Drawer v-model:open="menuOpen" side="right">
        <template #header>
			<header class="h-[72px] bg-white flex w-full items-center justify-between px-[clamp(24px,5vw,89px)]">
				<img
					:src="logo"
					alt="giarddesign"
					class="h-auto w-[128px]"
				/>
				<X :size="36" :stroke-width="1.5" @click="menuOpen = false"/>
			</header>
        </template>

         <nav aria-label="Główna nawigacja" class="flex flex-col gap-1 text-4xl font-normal px-[clamp(24px,5vw,89px)] py-16">
			<ul class="flex flex-col items-start gap-8">
				<li class="flex flex-col w-full">
					<button class="w-full flex justify-between items-center gap-1" @click="offerOpen = !offerOpen">
						Oferta
						<ChevronDown
							:size="36"
							:stroke-width="1.5"
							class="transition-transform duration-300 ease-out"
							:class="offerOpen && 'rotate-180'"
						/>
					</button>
					<div
						id="offer-panel"
						class="grid transition-all duration-300 ease-out"
						:class="offerOpen ? 'grid-rows-[1fr] opacity-100' : 'grid-rows-[0fr] opacity-0'"
					>
						<div class="overflow-hidden">
							<ul class="flex flex-col gap-4 pt-8 text-xl font-light">
								<li>
									<a @click="menuOpen = false" href="#services">Projekty</a>
								</li>
								<li>
									<a @click="menuOpen = false" href="#services">Wizualizacje</a>
								</li>
								<li>
									<a @click="menuOpen = false" href="#services">Realizacje</a>
								</li>
							</ul>
						</div>
					</div>
				</li>
				<li>
					<a @click="menuOpen = false" href="#about">O firmie</a>
				</li>
				<li>
					<a @click="menuOpen = false" href="#projects">Realizacje</a>
				</li>
				<li>
					<a @click="menuOpen = false" href="#contact">Kontakt</a>
				</li>
			</ul>
        </nav>
    </Drawer>
</template>