<script setup>
import { ArrowDown, ArrowLeft, ArrowRight } from 'lucide-vue-next'
import BaseButton from '../components/common/BaseButton.vue'
import heroImage from '../assets/images/hero.jpg'
</script>

<template>
    <section class="relative grid grid-cols-1 lg:grid-cols-2 h-[calc(100vh-72px)] overflow-hidden">
        <div class="flex items-center mt-auto mb-16 sm:mt-0 sm:mb-0 lg:bg-[var(--color-beige)]">
            <div class="w-full p-[clamp(24px,5vw,89px)]">
                <div class="flex flex-col gap-8">
                    <h1 class="hero-title w-full text-4xl sm:text-5xl lg:text-6xl leading-[1.25] font-medium text-white lg:text-black">
						<div>Nowoczesna aranżacja</div> 
						<div>Twojego ogrodu</div>
                    </h1>

                    <p class="max-w-[500px] text-sm sm:text-base leading-[1.65] text-white lg:text-black">
                        Marka GiardDesign to wieloletnie doświadczenie i wysoka
                        estetyka realizacji. Oferujemy kompleksowy zakres usług
                        z indywidualnym podejściem do każdego projektu.
                    </p>

                    <div class="flex flex-col sm:flex-row sm:items-center gap-3 md:gap-6 text-sm">
						<a href="#contact">
							<BaseButton>
								Skontaktuj się z nami
							</BaseButton>
						</a>

                        <div class="hidden lg:flex">
							<a href="#projects">
								<BaseButton outline class="gap-2 w-full">
									Zobacz nasze realizacje
									<ArrowDown :size="20" :stroke-width="1.5" />
								</BaseButton>
							</a>
						</div>

 						<div class="flex lg:hidden">
							<a href="#projects">
								<BaseButton variant="secondary" outline class="gap-2 w-full">
									Zobacz nasze realizacje
									<ArrowDown :size="20" :stroke-width="1.5" />
								</BaseButton>
							</a>
						</div>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="absolute lg:relative w-full h-full">
			<div class="absolute top-0 left-0 -z-10 w-full h-full hero-linear-gradient lg:hidden"></div>
			<div class="absolute inset-0 bg-[url('./assets/images/hero.jpg')] bg-position-[center bg-cover bg-no-repeat -z-20 lg:w-full"></div>
			<div class="absolute bottom-0 right-0 bg-[#F5F0EC] flex z-20">
				<button
					type="button"
					aria-label="Poprzedni slajd"
					class="flex h-16 lg:h-18 w-16 lg:w-18 items-center justify-center"
				>
					<ArrowLeft :size="32" :stroke-width="1.5" />
				</button>

				<button
					type="button"
					aria-label="Następny slajd"
					class="flex h-16 lg:h-18 w-16 lg:w-18 items-center justify-center"
				>
					<ArrowRight :size="32" :stroke-width="1.5" />
				</button>
			</div>
		</div>
    </section>
</template>