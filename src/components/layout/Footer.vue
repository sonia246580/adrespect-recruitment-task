<script setup>
import BaseButton from '../common/BaseButton.vue'
import BaseContainer from '../common/BaseContainer.vue'
import logo from '../../assets/images/logo.svg'
import adRespectLogo from '../../assets/images/adrespect.svg'
</script>

<template>
    <footer class="bg-[#111111] text-[#F5F0EC]">
        <BaseContainer>
            <div class="mx-auto w-full max-w-[1040px] py-12 md:py-14 lg:py-[72px]">
                <div
                    class="flex flex-col items-start gap-8 pb-10
                           md:flex-row md:items-center md:justify-between
                           md:gap-8 md:pb-12"
                >
                    <a
                        href="/"
                        aria-label="GiardDesign — strona główna"
                        class="shrink-0"
                    >
                        <img
                            :src="logo"
                            alt="GiardDesign"
                            class="h-auto w-[112px] brightness-0 invert"
                        />
                    </a>

                    <div
                        class="flex w-full flex-col items-start gap-6
                               md:w-auto md:flex-row md:items-center"
                    >
                        <p
                            class="max-w-[230px] text-[16px] leading-[24px]
                                   md:text-right"
                        >
                            Daj znać, co możemy dla Ciebie zrobić!
                        </p>

                        <BaseButton
                            class="w-full whitespace-nowrap md:w-auto"
                        >
                            Skontaktuj się z nami
                        </BaseButton>
                    </div>
                </div>

                <div class="h-px w-full bg-[#F5F0EC]/70"></div>

                <div class="pt-10 md:pt-12">
                    <div
                        class="flex flex-col items-center gap-10 text-center
                            md:flex-row md:items-start md:justify-between md:text-left"
                    >
                        <nav
                            aria-label="Linki w stopce"
                            class="flex flex-col items-center gap-4
                                text-[14px] leading-[21px]
                                md:flex-row md:items-center md:gap-12"
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

                        <div
                            class="flex flex-col items-center gap-3
                                text-[14px] leading-[21px] text-center
                                md:items-end md:text-right
                                lg:flex-row lg:items-center lg:gap-12"
                        >
                            <a
                                href="tel:000000000"
                                class="transition hover:opacity-70"
                            >
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

                    <div
                        class="mt-16 flex flex-col items-center gap-5
                            text-[14px] leading-[21px] text-center
                            md:mt-[104px] md:flex-row md:justify-between md:text-left"
                    >
                        <p>
                            Prawa zastrzeżone © 2022
                        </p>

                        <div class="flex items-center gap-2">
                            <span>made by</span>

                            <img
                                :src="adRespectLogo"
                                alt="adRespect"
                                class="h-[23px] w-auto"
                            />
                        </div>
                    </div>
                </div>
            </div>
        </BaseContainer>
    </footer>
</template>