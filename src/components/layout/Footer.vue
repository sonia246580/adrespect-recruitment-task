<script setup>
import BaseButton from '../common/BaseButton.vue'
import logo from '../../assets/images/logo.svg'
import BaseContainer from '../common/BaseContainer.vue';
</script>

<template>
    <footer class="bg-[#111111] text-[#F5F0EC]">
        <BaseContainer class="py-20"
            <div class="flex items-center justify-between pb-12">
                <img
                    :src="logo"
                    alt="GiardDesign"
                    class="h-auto w-[112px] brightness-0 invert"
                />

                <div class="flex items-center gap-6">
                    <p class="text-[16px]">
                        Daj znać, co możemy dla Ciebie zrobić!
                    </p>

                    <BaseButton>
                        Skontaktuj się z nami
                    </BaseButton>
                </div>
            </div>

            <div class="border-t border-[#F5F0EC]/70 pt-12">
                <div class="flex items-start justify-between">
                    <nav
                        aria-label="Linki w stopce"
                        class="flex items-center gap-12 text-[14px]"
                    >
                        <a href="#kontakt" class="transition hover:opacity-70">
                            Kontakt
                        </a>

                        <a href="#" class="transition hover:opacity-70">
                            Instagram
                        </a>

                        <a href="#" class="transition hover:opacity-70">
                            Facebook
                        </a>

                        <a href="#" class="transition hover:opacity-70">
                            LinkedIn
                        </a>
                    </nav>

                    <div class="flex items-center gap-12 text-[14px]">
                        <a href="tel:000000000" class="transition hover:opacity-70">
                            000-000-000
                        </a>

                        <a
                            href="mailto:giarddesign@kontakt.pl"
                            class="transition hover:opacity-70"
                        >
                            giarddesign@kontakt.pl
                        </a>
                    </div>
                </div>

                <div class="mt-20 flex items-center justify-between text-[14px]">
                    <p>
                        Prawa zastrzeżone © 2022
                    </p>

                    <p class="flex items-center gap-2">
                        made by
                        <span class="text-[18px] font-medium">
                            adRespect
                        </span>
                    </p>
                </div>
            </div>
        </BaseContainer>
    </footer>
</template>