<script setup>
import Header from './components/layout/Header.vue'
import Footer from './components/layout/Footer.vue'
import HeroSection from './sections/HeroSection.vue'
import ServiceSection from './sections/ServiceSection.vue'
import AboutSection from './sections/AboutSection.vue'
import ProjectsSection from './sections/ProjectsSection.vue'
import InstagramSection from './sections/InstagramSection.vue'
</script>

<template>
  <Header />

  <main>
    <HeroSection/>
    <ServiceSection id="services"/>
    <AboutSection id="about"/>
    <ProjectsSection id="projects"/>
    <InstagramSection id="contact"/>
  </main>

  <Footer />
</template>